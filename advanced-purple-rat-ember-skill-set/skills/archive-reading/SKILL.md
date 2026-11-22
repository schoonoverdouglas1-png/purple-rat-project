---
name: archive_reading
description: Read and rate the inside of archive files (zip, tar, tar.gz, gz; cab detected) without unpacking them, in all places Ember works.
---
# Archive Reading — taught Nov 16, 2026, at Douglas's "make it so"
Tool: `~/workspace/tools/archive-peek.py <archive> [--read <entry-substring>] [--lines N]`
- Lists every entry with size and a rating (the tool's labeled heuristic: 5 = md/txt daily working files, 4 = data, 3 = media/docs, 2 = code/config, 1 = binary, 0 = empty).
- `--read` prints the text of a matching entry from INSIDE the archive — nothing is unpacked to disk.
- Formats: .zip, .tar, .tar.gz/.tgz, .tar.bz2, .tar.xz, .gz verified on this box (zip/tar/gzip + Python zipfile/tarfile).
- .cab: NO extractor installed (cabextract, 7z, gcab, bsdtar all checked absent, Nov 16 2026). The tool detects .cab and says so plainly. Installing cabextract is a system change — Douglas's explicit word first.
- Pairs with the scratch space (`~/workspace/scratch-space/`, ACCESS.md): archives are working surfaces, not sealed boxes.
