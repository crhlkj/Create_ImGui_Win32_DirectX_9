cmake_minimum_required(VERSION 3.31)
project(YourNameProject)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

set(IMGUI_DIR ${CMAKE_SOURCE_DIR}/include/imgui)
set(IMGUI_SOURCES
        ${IMGUI_DIR}/imgui.cpp
        ${IMGUI_DIR}/imgui_draw.cpp
        ${IMGUI_DIR}/imgui_tables.cpp
        ${IMGUI_DIR}/imgui_widgets.cpp
        ${IMGUI_DIR}/imgui_demo.cpp
        ${IMGUI_DIR}/backends/imgui_impl_dx9.cpp
        ${IMGUI_DIR}/backends/imgui_impl_win32.cpp
)

add_library(imgui STATIC ${IMGUI_SOURCES})

target_include_directories(imgui
        PUBLIC
        ${IMGUI_DIR}
        ${IMGUI_DIR}/backends
)

add_executable(${PROJECT_NAME} src/main.cpp)
target_link_libraries(${PROJECT_NAME}
        PRIVATE
        imgui
        d3d9
        dwmapi
)
