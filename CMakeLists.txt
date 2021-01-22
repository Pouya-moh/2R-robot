project(2R-robot)
cmake_minimum_required(VERSION 3.10)

set(OpenGL_GL_PREFERENCE GLVND)

find_package(GLEW REQUIRED)
find_package(OpenGL REQUIRED)

add_executable(imtest
        imgui/imgui.cpp
        imgui/imgui_draw.cpp
        imgui/imgui_demo.cpp
        imgui/imgui_tables.cpp
        imgui/imgui_widgets.cpp

        imgui/backends/imgui_impl_sdl.cpp
        imgui/backends/imgui_impl_opengl3.cpp

        imgui/examples/example_sdl_opengl3/main.cpp
        )

target_include_directories(imtest PRIVATE imgui)
target_include_directories(imtest PRIVATE imgui/backends)
target_include_directories(imtest PRIVATE /usr/include/SDL2)
target_include_directories(imtest PRIVATE /usr/include/GL)
target_link_libraries(imtest ${GLEW_LIBRARIES} ${OPENGL_LIBRARIES} SDL2)

add_executable(2R-robot
        main.cpp

        imgui/imgui.cpp
        imgui/imgui_draw.cpp
        imgui/imgui_tables.cpp
        imgui/imgui_widgets.cpp

        imgui/backends/imgui_impl_sdl.cpp
        imgui/backends/imgui_impl_opengl3.cpp
        )


target_include_directories(2R-robot PRIVATE imgui)
target_include_directories(2R-robot PRIVATE imgui/backends)
target_include_directories(2R-robot PRIVATE /usr/include/SDL2)
target_include_directories(2R-robot PRIVATE /usr/include/GL)
target_link_libraries(2R-robot ${GLEW_LIBRARIES} ${OPENGL_LIBRARIES} SDL2)