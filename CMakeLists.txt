cmake_minimum_required(VERSION 3.10)

project(ImGuiTest1 LANGUAGES CXX)

add_executable(ImGuiTest1 src/main.cpp)


# GLFW (compile)
set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
target_link_libraries(ImGuiTest1 glfw)

# OpenGL
find_package(OpenGL REQUIRED)
target_link_libraries(ImGuiTest1 OpenGL::GL)

# imgui
target_link_libraries(ImGuiTest1 imgui)

add_subdirectory(lib)
