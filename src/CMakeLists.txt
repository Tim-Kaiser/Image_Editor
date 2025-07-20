add_executable(ImageEditor main.cpp Window.cpp Window.h)

target_link_libraries(ImageEditor PUBLIC SFML::Graphics SFML::Audio ImGui-SFML::ImGui-SFML)

include(Install.cmake)