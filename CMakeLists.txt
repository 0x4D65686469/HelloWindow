cmake_minimum_required(VERSION 3.10)
project(HelloWindow)

set(CMAKE_CXX_STANDARD 17)

add_executable(HelloWindow src/main.cpp src/glad.c)

target_include_directories(HelloWindow PRIVATE include)
target_link_libraries(HelloWindow PRIVATE 
    ${CMAKE_SOURCE_DIR}/lib/libglfw3dll.a
    opengl32
    gdi32
)

add_custom_command(TARGET HelloWindow POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy
    ${CMAKE_SOURCE_DIR}/lib/glfw3.dll
    $<TARGET_FILE_DIR:HelloWindow>
)