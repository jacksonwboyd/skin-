# Physical Drum Engine — Final Native Build

This is the native JUCE project for the full-kit version.

## Targets
- macOS Standalone
- AU
- VST3

## Build on macOS
1. Install Xcode Command Line Tools.
2. Install CMake.
3. Open Terminal in this folder.
4. Run:
   `cmake -B build -G Xcode`
5. Build:
   `cmake --build build --config Release`
6. Open the generated Standalone app from the build products.

JUCE is fetched automatically by CMake at configure time.

## MIDI / kit
The engine has 12 MIDI-mapped pads:
Kick 36, Snare 38, Closed Hat 42, Open Hat 46, Tom 1 45, Tom 2 43, Tom 3 41, Crash 49, Ride 51, Clap 39, Perc 1 37, Perc 2 40.

Each pad has a LOAD button so the full kit can be populated with separate WAVs. Incoming MIDI note-on velocity drives that pad's physical-response engine.

The supplied snare is preloaded into the Snare slot.

## Important
This is a substantial native V1 architecture, but it is not claiming to reproduce NEST/SKIN's proprietary DSP. The physical model is an original implementation. The next engineering pass should add true offline sample analysis (transient/body/tail extraction), velocity layers, round-robin selection, hat choking, per-pad controls, and higher-quality interpolation/resynthesis.
