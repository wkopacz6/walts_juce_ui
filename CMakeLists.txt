cmake_minimum_required(VERSION 3.20)

project(walts_juce_ui VERSION 1.0.0 LANGUAGES CXX
        DESCRIPTION "JUCE module containing some JUCE UI elements that I might want to reuse"
        HOMEPAGE_URL "https://github.com/wkopacz6/walts_juce_ui")

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED YES)


if (NOT COMMAND juce_add_module)
    message(FATAL_ERROR "JUCE must be added to your project before adding a module!")
endif ()

# juce_add_module(submodules/melatonin_blur)
# add_library(melatonin_blur STATIC submodules/melatonin_blur/melatonin_blur.cpp)
juce_add_module("${CMAKE_CURRENT_LIST_DIR}")

# Add BinaryData for walts_juce_ui
file(GLOB_RECURSE WaltsUiAssetFiles CONFIGURE_DEPENDS "${CMAKE_CURRENT_SOURCE_DIR}/Assets/*")
juce_add_binary_data(WaltsUiBinaryData SOURCES ${WaltsUiAssetFiles} HEADER_NAME WaltsUiBinaryData.h NAMESPACE WaltsUiBinaryData)
