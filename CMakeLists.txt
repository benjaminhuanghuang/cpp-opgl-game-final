cmake_minimum_required(VERSION 3.7)

project(spacecraft.exe VERSION 1.0.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${PROJECT_SOURCE_DIR}/cmake/")

project(cpp-opgl-game)

find_package(SDL2 REQUIRED)
find_package(SDL2_image REQUIRED)
find_package(SDL2_ttf REQUIRED)

find_package(GLEW REQUIRED)
find_package(OPENGL REQUIRED)


if(SDL2_FOUND)
  message(STATUS "Find SDL2: ${SDL2_INCLUDE_DIRS}")
else()
  message(STATUS "Can not find SDL2") 
endif()


include_directories(${SDL2_INCLUDE_DIRS})
include_directories(${SDL2_IMAGE_INCLUDE_DIRS})
include_directories(${SDL2_TTF_INCLUDE_DIRS})


set(FMOD_LINCLUDE_DIR "/Users/bhuang/FMOD/api/studio/inc")
set(FMOD_LIBRARY "/Users/bhuang/FMOD/api/studio/lib/libfmodstudio.dylib")
set(FMOD_CORE_LINCLUDE_DIR "/Users/bhuang/FMOD/api/core/inc")
set(FMOD_CORE_LIBRARY "/Users/bhuang/FMOD/api/core/lib/libfmod.dylib")

#=================== INCLUSION OF Project Files ================#
set(SOURCE_DIR "${CMAKE_SOURCE_DIR}/src")

file(GLOB_RECURSE SOURCES
    "${SOURCE_DIR}/*.h"
    "${SOURCE_DIR}/*.cpp"
)

add_executable(${CMAKE_PROJECT_NAME} ${SOURCES})

#===================== LINKING LIBRARIES =======================#
target_link_libraries(${CMAKE_PROJECT_NAME} 
                        ${SDL2_LIBRARY}
                        ${SDL2_IMAGE_LIBRARY}
                        ${SDL2_TTF_LIBRARY}
                        ${OPENGL_LIBRARY}
                        ${GLEW_LIBRARY}
                        ${SOIL_LIBRARY}
                        ${FMOD_LIBRARY}
                        ${FMOD_CORE_LIBRARY}
                        )