
cmake_minimum_required(VERSION 3.10.2)

project("sdlhello")

add_subdirectory(SDL)
add_subdirectory(SDL_image)

#add_subdirectory(SDL_mixer)
#add_subdirectory(SDL_ttf)

add_library( # Sets the name of the library.
        sdlhello
        SHARED
        main.cpp)

find_library(SDL2 SDL2)
find_library(SDL2_image SDL2_image)
find_library(log-lib log)

include_directories(${CMAKE_SOURCE_DIR}/SDL/include)
include_directories(${CMAKE_SOURCE_DIR}/SDL_image)

# Specifies libraries CMake should link to your target library. You
# can link multiple libraries, such as libraries you define in this
# build script, prebuilt third-party libraries, or system libraries.

target_link_libraries(sdlhello ${log-lib} SDL2 SDL2_image)
