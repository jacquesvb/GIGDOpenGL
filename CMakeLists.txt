cmake_minimum_required(VERSION 3.16)
project(hello_window VERSION 1.0.0)

find_package(OpenGL REQUIRED)

add_executable(
    hello_window 
    src/config.h 
    src/main.cpp 
    src/glad.c
    src/triangle_mesh.h
    src/triangle_mesh.cpp
)

target_include_directories(hello_window PRIVATE
    dependencies
    dependencies/glm
)

# Absolute path to the shader sources, so the executable finds them no matter
# which directory it is started from.
target_compile_definitions(hello_window PRIVATE
    SHADER_DIR="${CMAKE_CURRENT_SOURCE_DIR}/src/shaders"
)

target_link_libraries(hello_window PRIVATE
    glfw
    OpenGL::GL
)
