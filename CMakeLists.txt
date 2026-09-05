cmake_minimum_required(VERSION 3.22)
project(PhysicalDrumEngine VERSION 1.0.0)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include(FetchContent)
FetchContent_Declare(
  JUCE
  GIT_REPOSITORY https://github.com/juce-framework/JUCE.git
  GIT_TAG 8.0.12
  GIT_SHALLOW TRUE
)
FetchContent_MakeAvailable(JUCE)

juce_add_plugin(PhysicalDrumEngine
    COMPANY_NAME "Independent"
    PRODUCT_NAME "Physical Drum Engine"
    BUNDLE_ID "com.independent.physicaldrumengine"
    PLUGIN_MANUFACTURER_CODE Pdem
    PLUGIN_CODE Pde1
    FORMATS AU VST3 Standalone
    IS_SYNTH TRUE
    NEEDS_MIDI_INPUT TRUE
    NEEDS_MIDI_OUTPUT FALSE
    IS_MIDI_EFFECT FALSE
    COPY_PLUGIN_AFTER_BUILD TRUE
)

juce_add_binary_data(PhysicalDrumEngineData
    SOURCES Assets/snare.wav
)

juce_generate_juce_header(PhysicalDrumEngine)

target_sources(PhysicalDrumEngine PRIVATE
    Source/PluginProcessor.cpp
    Source/PluginEditor.cpp
)

target_compile_definitions(PhysicalDrumEngine PRIVATE
    JUCE_WEB_BROWSER=0
    JUCE_USE_CURL=0
    JUCE_VST3_CAN_REPLACE_VST2=0
)

target_link_libraries(PhysicalDrumEngine PRIVATE
    juce::juce_audio_utils
    juce::juce_dsp
    PhysicalDrumEngineData
)
