# Minimum CMake version
cmake_minimum_required(VERSION 3.10)

# Project name
project(mfcc_project)

# Set the C standard (if required)
# set(CMAKE_C_STANDARD 99)
set(CMAKE_CXX_STANDARD 11)

# Add include directories
include_directories(${CMAKE_SOURCE_DIR})
include_directories(${CMAKE_SOURCE_DIR}/BasicAudioToolBox)
include_directories(${CMAKE_SOURCE_DIR}/inih)

# Add the executable and the list of source files
add_executable(mfcc
    main.cpp
    BasicAudioToolBox/hmath.c
    inih/ini.c
    mfcc.c
    BasicAudioToolBox/sigProcess.c
    BasicAudioToolBox/WAVE.c
)

# Link the math library (libm)
target_link_libraries(mfcc m)

# Optionally, define a custom clean command
add_custom_target(cleanup
    COMMAND ${CMAKE_COMMAND} -E rm -f mfcc *.o
)
