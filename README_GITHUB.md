# Physical Drum Engine — GitHub Mac Builder

This repository is designed to build the plugin on a GitHub-hosted macOS runner, so the local Mac does **not** need Xcode or Xcode Command Line Tools. GitHub Actions provides macOS runners with Apple development tooling.

## No-Terminal setup

1. Create a GitHub account at github.com if you do not already have one.
2. Create a new repository named `physical-drum-engine`.
3. Upload the contents of this folder to the repository.
4. Open the repository's **Actions** tab.
5. Select **Build Physical Drum Engine**.
6. Click **Run workflow**.
7. Wait for the green checkmark.
8. Open the completed workflow run and download the **Physical-Drum-Engine-macOS** artifact.
9. Unzip it on the Mac.

The build is configured as a Universal macOS binary (Apple Silicon + Intel) and requests AU, VST3, and Standalone formats.

The factory snare is embedded into the plugin binary, so the installed plugin does not need the original Assets folder.

## Install on Mac

- `.component` → `~/Library/Audio/Plug-Ins/Components/`
- `.vst3` → `~/Library/Audio/Plug-Ins/VST3/`
- `.app` → Applications or any convenient folder

Then restart Logic Pro and use **Plug-in Manager** to rescan if necessary.

## Important

This build is the current native prototype. It contains the 12-pad MIDI architecture, shared physical response engine, and per-pad sample loading UI. The next development pass will expand the kit to multiple samples/velocity layers and round-robin behavior.
