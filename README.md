# nerion-android-jdk-build

Builds our own OpenJDK 21 for Android, from source, per-ABI, and publishes a
`JreManifest`-shaped Release consumed at runtime by
[`feeldev12/launcher`](https://github.com/feeldev12/launcher)'s Android JRE
provisioning (`src-tauri/src/android/jre.rs`).

Separate repo from
[`nerion-android-renderer`](https://github.com/feeldev12/nerion-android-renderer),
mirroring AngelAuraMC's own `angelauramc-openjdk-build` /
`amethyst-prebuilt-libraries` split — independent cadence, size, and
licensing surface per artifact (design D2). This repo has no vendored
binaries and no licensing gate: OpenJDK is GPLv2+Classpath-Exception and we
build entirely from source ourselves (design D7).

## What this produces

Per-ABI OpenJDK 21 JDK + JRE `.tar.xz` archives (+ `.sha256`), plus a
`jre21-manifest.json` describing them, all published to the `jre21-android`
GitHub Release tag on this repo.

## Build recipe

Ported near-verbatim from `feeldev12/launcher`'s private
`.github/workflows/android-jdk21.yml` (task B2) — see
`.github/workflows/jre21-android.yml`'s own header comment for the exact
diff. Builds from a pinned commit of
[`AngelAuraMC/angelauramc-openjdk-build`](https://github.com/AngelAuraMC/angelauramc-openjdk-build)
(`buildjre17-21` branch) as the reference build recipe.
