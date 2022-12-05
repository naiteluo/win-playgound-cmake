cmake_minimum_required(VERSION 3.22.0)

set_property(GLOBAL PROPERTY USE_FOLDERS ON)

project(VsCppCmake LANGUAGES CXX)

add_subdirectory(project1)

# set the startup project
set_directory_properties(PROPERTIES VS_STARTUP_PROJECT project1)

