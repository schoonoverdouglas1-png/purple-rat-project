# Disc Image Reading — Reading ISO/qcow2 Images Without Mounting

> **Author: Ember, from verified work Nov 12, 2026, guided by Douglas.**
> Version: 1.0 · Updated: 2026-11-12
> Changelog: v1.0 2026-11-12 — first version, distilled from the verified mounting study in `~/workspace/machines/LEARNING-LOG-2026-11-12.md` ("MOUNTING IMAGES — learned by doing") and Module 1 snapshot work the same evening.
> Credit kept per the Captain's copyright doctrine: kept and shared both.

## The headline fact about this box

**True loop-mounting is impossible here.** Verified Nov 12, 2026: no `/dev/loop*` devices exist at all (and no `/dev/nbd*`). `mount -o loop,ro <iso> <mnt>` failed with exit 32 ("mount failed: No such file or directory" — the mount binary is fine; the kernel devices it needs were never granted in this sandbox), and it was verified afterwards that nothing was ever mounted (`mount | grep <name>` empty).

So on this box, **"mounting an image" means reading its format directly** — no kernel help needed. Do not burn time retrying loop or nbd until the box's `/dev` changes; retest then, dated.

## Reading an ISO — `iso_inventory.py`

Tool: `~/workspace/machines/iso_inventory.py` — pure Python stdlib, read-only, written for this job (no `pycdlib` on the box).

- Inventory: `python3 ~/workspace/machines/iso_inventory.py <image.iso>`
- Print one file: `python3 ~/workspace/machines/iso_inventory.py <image.iso> --cat /isolinux/isolinux.cfg`

Verified cold on the Warty ISO (`warty-release-install-amd64.iso`): full ISO9660/Joliet walk — `/isolinux/` (isolinux.bin 9,396 B, boot.cat, splash.rle, f1.txt–f10.txt help screens) and `isolinux.cfg` read in full (`DEFAULT /install/vmlinuz`; boot parameters live on its APPEND line — that's where round-2 `noapic`/`acpi=off` go).

The ISO is only ever read, never written.

## Reading a qcow2 — `qemu-img`, copies only

- Metadata: `qemu-img info --force-share <disk.qcow2>`
  - Plain `qemu-img info` **refuses** a disc a running guest holds (write lock) — that refusal is correct behavior, not an error to defeat. `--force-share` is the read-only road in. Verified on `warty-disk.qcow2` held by the live Warty guest: qcow2 v3 (compat 1.1, zlib, cluster 65,536), not corrupt, no dirty flag, snapshot `warty-firstboot` listed.
- Partitions/content: `qemu-img convert --force-share -O raw <disk.qcow2> /tmp/<copy>.raw` — **always on a copy in scratch (/tmp), never on the original** — then parse at offsets in Python (MBR partition table at offset 446; 0x55AA signature check). **Delete the raw copy when done.** Verified: the Warty disc read as completely blank (no signature, all partition entries zero) — exactly right, since its kernel stalls before the installer ever writes.
- qcow2 is sparse copy-on-write: a freshly created 64 MiB test disc used 196 KiB on disk (proven by `qemu-img create` + `info`, Module 1).

## Snapshot rules (learned from a failure)

- A **CD-only guest cannot snapshot itself**: `savevm` failed with "no block device can store vmstate for snapshot." Guests that need snapshots must carry a qcow2 disc. With a disc attached, `savevm pic-snap` succeeded (snapshot 2.48 MiB, listed in the monitor's `info snapshots`).
- Check a live guest's snapshots through its **monitor** (`info snapshots`), not `qemu-img info` (write lock).
- Snapshot before anything wild (Reversibility Rule); scratch and experimental work lives inside the guests or in clearly-marked scratch areas — the main box stays the clean archive (VM scratch-space doctrine, Nov 12, 2026).

## Tool gaps on this box (dated Nov 12, 2026 — do NOT install; study gate)

`isoinfo`, `xorriso`, `bsdtar`, `7z`, `guestmount`, `fdisk`/`sfdisk`/`parted`, `hexdump`/`xxd`, `pycdlib`. Present and sufficient: `qemu-img`, `file`, `tar`, `od`, `strings`, Python 3.12 stdlib. `qemu-nbd` exists as a binary but is useless here (no `/dev/nbd*`).

## The Guard

Everything in this skill is read-only against originals. Conversions happen on copies in scratch. No command here deletes, converts in place, or writes to a source image — if a step would, it stops at the Guard like everything else.
