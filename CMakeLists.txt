cmake_minimum_required(VERSION 3.16)

project(imsearch LANGUAGES CXX)

add_library(imsearch STATIC
    imsearch.cpp
)

target_include_directories(imsearch
    PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR}
)

target_compile_features(imsearch PUBLIC cxx_std_20)

find_package(imgui CONFIG QUIET)
if(TARGET imgui::imgui)
    target_link_libraries(imsearch PUBLIC imgui::imgui)
endif()

add_library(imsearch::imsearch ALIAS imsearch)

