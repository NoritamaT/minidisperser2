cmake_minimum_required(VERSION 3.22)
project(MiniDisperser VERSION 1.0.0)

include(FetchContent)
FetchContent_Declare(JUCE
    GIT_REPOSITORY https://github.com/juce-framework/JUCE.git
    GIT_TAG 8.0.4)
FetchContent_MakeAvailable(JUCE)

juce_add_plugin(MiniDisperser
    COMPANY_NAME "MyCompany"
    PLUGIN_MANUFACTURER_CODE Mycn
    PLUGIN_CODE Mdsp
    FORMATS VST3 AU Standalone
    PRODUCT_NAME "Mini Disperser"
    IS_SYNTH FALSE
    NEEDS_MIDI_INPUT FALSE)

target_sources(MiniDisperser PRIVATE
    Source/PluginProcessor.cpp
    Source/PluginEditor.cpp)

target_compile_definitions(MiniDisperser PUBLIC
    JUCE_WEB_BROWSER=0
    JUCE_USE_CURL=0
    JUCE_VST3_CAN_REPLACE_VST2=0)

target_link_libraries(MiniDisperser PRIVATE
    juce::juce_audio_utils
    juce::juce_dsp
    PUBLIC
    juce::juce_recommended_config_flags
    juce::juce_recommended_warning_flags)
