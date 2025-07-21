cmake_minimum_required(VERSION 3.10)
project(ImageEditor VERSION 0.1)

include(FetchContent)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)

set(INCLUDE_DIRECTORIES ./)
include_directories(lib)

set(FETCHCONTENT_BASE_DIR ${PROJECT_SOURCE_DIR}/lib CACHE PATH "Sets the FETCHCONTENT_BASE_DIR to /lib." FORCE)

FetchContent_Declare(SFML
                     GIT_REPOSITORY https://github.com/SFML/SFML.git
                     GIT_TAG 3.0.1
                     GIT_SHALLOW ON
                     EXCLUDE_FROM_ALL
                     SYSTEM)
FetchContent_MakeAvailable(SFML)

FetchContent_Declare(assimp
                     GIT_REPOSITORY https://github.com/assimp/assimp.git
                     GIT_TAG master)
    set(BUILD_SHARED_LIBS OFF CACHE BOOL "" FORCE)
    set(ASSIMP_BUILD_TESTS OFF CACHE BOOL "" FORCE)
    set(ASSIMP_INJECT_DEBUG_POSTFIX OFF CACHE BOOL "" FORCE)
    set(ASSIMP_INSTALL OFF CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(assimp)

add_executable(ImageEditor
               src/Window.h
               src/include/glad/gl.h
               src/include/KHR/khrplatform.h
               src/Window.cpp
               src/main.cpp)

target_include_directories(ImageEditor PRIVATE
                           ${PROJECT_SOURCE_DIR}/lib/assimp-src/include
                           ${PROJECT_SOURCE_DIR}/lib/sfml-src/include )

target_link_libraries(ImageEditor PRIVATE
                      SFML::Graphics
                      SFML::Audio
                      assimp)