
cmake_minimum_required(VERSION 3.10.2)

project("sdlhello")

#add_subdirectory(SDL)
#add_subdirectory(SDL_image)
#add_subdirectory(SDL_mixer)
#add_subdirectory(SDL_ttf)

add_library( # Sets the name of the library.
        sdlhello
        SHARED
        main.cpp)

#find_library(SDL2 SDL2)
#find_library(SDL2_image SDL2_image)
find_library(log-lib log)

#include_directories(${CMAKE_SOURCE_DIR}/SDL/include)
#include_directories(${CMAKE_SOURCE_DIR}/SDL_image)

# Find fmt
FIND_PACKAGE(fmt CONFIG REQUIRED HINTS ${DEPENDENCIES} NO_CMAKE_FIND_ROOT_PATH)

# Find Swan
FIND_PACKAGE(Swan CONFIG REQUIRED HINTS ${DEPENDENCIES} NO_CMAKE_FIND_ROOT_PATH)

# Find SDL2
FIND_PACKAGE(SDL2 CONFIG REQUIRED HINTS ${DEPENDENCIES} NO_CMAKE_FIND_ROOT_PATH)

# Find SDL2_image
#FIND_PACKAGE(SDL2_image CONFIG REQUIRED HINTS ${DEPENDENCIES} NO_CMAKE_FIND_ROOT_PATH)

TARGET_INCLUDE_DIRECTORIES (sdlhello
        PUBLIC ${Swan_INCLUDE_DIRS}
        PUBLIC ${SDL2_INCLUDE_DIRS})
#        PUBLIC ${SDL2_image_INCLUDE_DIRS})

# Specifies libraries CMake should link to your target library. You
# can link multiple libraries, such as libraries you define in this
# build script, prebuilt third-party libraries, or system libraries.

target_link_libraries(sdlhello
        PRIVATE ${SWAN_LIBRARIES}
        PRIVATE SDL2::SDL2-static
        ${DEPENDENCIES}/lib/libSDL2_image.a
        ${DEPENDENCIES}/lib/libpng16.a
        ${DEPENDENCIES}/lib/libz.a
        ${log-lib})
