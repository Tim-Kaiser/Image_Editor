set(SFML_VERSION 3.0.1)
set(IMGUI_VERSION v1.92.1)
set( IMGUI_SFML_VERSION  v2.6.1)

include(FetchContent)

FetchContent_Declare(SFML
                     GIT_REPOSITORY https://github.com/SFML/SFML.git
                     GIT_TAG ${SFML_VERSION}
                     GIT_SHALLOW ON
                     EXCLUDE_FROM_ALL
                     SYSTEM)

FetchContent_Declare(imgui
                     GIT_REPOSITORY https://github.com/ocornut/imgui.git
                     GIT_TAG ${IMGUI_VERSION}
                     GIT_SHALLOW ON
                     EXCLUDE_FROM_ALL
                     SYSTEM)

FetchContent_Declare(imgui-sfml
                     GIT_REPOSITORY https://github.com/SFML/imgui-sfml.git
                     GIT_TAG ${IMGUI_SFML_VERSION}
                     GIT_SHALLOW ON
                     EXCLUDE_FROM_ALL
                     SYSTEM)

option( SFML_BUILD_NETWORK "build network" OFF)
option(SFML_BUILD_AUDIO "Build audio" ON)
FetchContent_MakeAvailable(sfml)

FetchContent_MakeAvailable(imgui)

set(IMGUI_DIR ${imgui_SOURCE_DIR})
option(IMGUI_SFML_FIND_SFML "Use find_package to find SFML" OFF)
option(IMGUI_SFML_IMGUI_DEMO "Build imgui_demo.cpp" OFF)

FetchContent_MakeAvailable(imgui-sfml)