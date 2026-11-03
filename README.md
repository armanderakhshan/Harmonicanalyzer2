# Harmonic Analyzer (AU / VST3 / Standalone) for macOS

Analyzes a song: key, BPM, chords, and Camelot-wheel harmonic mixing suggestions.

## Get the .dmg (no Xcode needed)
1. Create a free GitHub repo and upload the contents of this folder (keep `.github/`).
2. Open the **Actions** tab, run **Build macOS DMG** (also runs on every push to `main`).
3. When it finishes, download the **HarmonicAnalyzer-dmg** artifact: it contains `HarmonicAnalyzer.dmg`.

## Build locally (macOS + Xcode command line tools + CMake)
    cmake -B build -DCMAKE_BUILD_TYPE=Release && cmake --build build --config Release -j 8

## Install
- Open the DMG. Drag `Harmonic Analyzer.component` into `/Library/Audio/Plug-Ins/Components`,
  the `.app` into Applications.
- The build is ad-hoc signed, not notarized. If macOS blocks it:
  `xattr -cr "/Applications/Harmonic Analyzer.app" "/Library/Audio/Plug-Ins/Components/Harmonic Analyzer.component"`
- Validate for Logic: `auval -v aufx Hanl Hmix`. In Logic: Audio FX > Audio Units > HarmonicMix > Harmonic Analyzer.
  (Logic > Settings > Plug-in Manager > Reset & Rescan if needed.)

## Use
- Standalone or plugin: **Load song file...** (or drag a file onto the window).
- In Logic: **Start live capture**, play the song, **Stop & Analyze** (needs 10 s+; the plugin passes audio through untouched).
