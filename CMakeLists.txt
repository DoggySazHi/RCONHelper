﻿cmake_minimum_required (VERSION 3.8)

project ("RCONHelper")

if(CMAKE_BUILD_TYPE MATCHES Debug)
    message("Optimizations off!")
    set(CMAKE_C_FLAGS_DEBUG "${CMAKE_C_FLAGS_DEBUG} -O0")
    set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -O0")
else()
    message("Optimizations on!")
    set(CMAKE_CXX_FLAGS_RELEASE "-O3")
endif()

if(MSVC)
    message("Using MSVC!")
    find_package(OpenCV REQUIRED)
    # If you have a custom OpenCV path (i.e. you downloaded it from the website, use)
    # find_package(OpenCV REQUIRED PATHS "C:\\Users\\username\\opencv\\build" NO_DEFAULT_PATH)
else()
    message("Using non-MSVC!")
    find_package(OpenCV REQUIRED)
    # If you have a custom OpenCV path (i.e. you compiled it yourself, use)
    # set(OpenCV_DIR /home/username/opencv/build)
    # find_package(OpenCV REQUIRED PATHS "/home/username/opencv/build" NO_DEFAULT_PATH)
endif()

include_directories(${OpenCV_INCLUDE_DIRS})
# Download and build https://github.com/craigsapp/midifile, then include it.
include_directories(/home/username/midifile/include)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

file(GLOB RCONHelper_SRC
        "src/RCONHelper/*.c"
        "src/RCONHelper/*.cpp"
        "src/RCONHelper/*.c"
        )

file(GLOB RCONHelper_Test_SRC
        "src/RCONHelper/*.h"
        "src/RCONHelper/*.cpp"
        "src/RCONHelper/*.c"
        "src/RCONHelper_Test/*.h"
        "src/RCONHelper_Test/*.cpp"
        "src/RCONHelper_Test/*.c"
        )

add_library(RCONHelper SHARED ${RCONHelper_SRC})
add_executable(RCONHelper_Test ${RCONHelper_Test_SRC})

if(MSVC)
    target_compile_options(RCONHelper PRIVATE /W4 /WX /std:c++20)
else()
    target_compile_options(RCONHelper PRIVATE -Wall -Wextra -pedantic -Werror -std=c++20)
    SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pthread")
endif()

target_link_libraries(RCONHelper_Test ${OpenCV_LIBS})
# Also check here for the midifile library.
target_link_libraries(RCONHelper_Test /home/username/midifile/lib/libmidifile.a)

set_property(TARGET RCONHelper PROPERTY CXX_STANDARD 20)
set_property(TARGET RCONHelper PROPERTY CXX_STANDARD_REQUIRED 20)
set_property(TARGET RCONHelper_Test PROPERTY CXX_STANDARD 20)
set_property(TARGET RCONHelper_Test PROPERTY CXX_STANDARD_REQUIRED 20)