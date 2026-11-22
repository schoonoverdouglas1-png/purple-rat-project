# APK Building — the hand-rolled pipeline (taught Nov 16, 2026, Douglas's developer order)

Build minimal, installable, signed APKs with no Gradle and no bloat: manifest + Java + the SDK tools, nothing else. Douglas's rule: functionality over extra anything; he is a developer and Ember builds this way for certain.

## The toolchain (all verified live Nov 16, 2026)
- JDK 17 (Temurin) at `~/workspace/tools/jdk` — set JAVA_HOME to it. The portable JRE beside it cannot compile.
- Android SDK at `~/workspace/tools/android-sdk`: platform android-30 (`platforms/android-30/android.jar`), build-tools 30.0.3 (aapt, d8, zipalign, apksigner).
- One command does the whole build: `bash ~/workspace/tools/build-apk.sh <project-src-dir> <keystore> <out.apk>` — packages the manifest, compiles with `javac --release 8` (build-tools 30's d8 rejects Java 17 class files, major version 61 — the release flag is the fix), dexes with d8 --lib, zipaligns, signs, and verifies.

## Signing — the key is the identity
- Android only accepts an update to an installed app when the new APK carries the SAME signing key. Pick a key per app line and never lose it.
- Purple Rat WebKit line: `~/workspace/purple-rat-webkit/src/webkit-debug.keystore` (alias androiddebugkey, standard debug passwords) — generated Nov 16, 2026; every WebKit build signs with it.
- Douglas's Nov 14 keystore (purple-rat-mail/console/research) has a non-standard password Ember does not know. Never ask for it in chat — credentials move only through the Secure Vault. Without it, those three apps can be rebuilt only under a new key, which means uninstall-then-reinstall on the phone.
- Debug-signed APKs sideload fine (tap the file, allow install). Stores and F-Droid's public catalog are later, separate, and only at Douglas's word after testing.

## Project shape
`src/AndroidManifest.xml`, `src/<package path>/MainActivity.java`, keystore beside them. First proof: PurpleRatWebKit-debug.apk, 8,559 bytes, com.purplerat.webkit v1.0, signature verified Nov 16, 2026.
