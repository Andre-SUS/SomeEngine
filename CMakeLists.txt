cmake_minimum_required(VERSION 3.2)

set(PROJECT_NAME SomeEngine)
project(${PROJECT_NAME} C CXX)

#find_package(glfw3 REQUIRED)
#find_package(imgui REQUIRED)

add_executable(${PROJECT_NAME} 
  sources/main.cpp
  sources/imgui.cpp
  sources/imgui_draw.cpp
  sources/imgui_impl_glfw.cpp
  sources/imgui_impl_opengl3.cpp
  sources/imgui_tables.cpp
  sources/imgui_widgets.cpp
  )

set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
set(GLFW_INSTALL OFF CACHE BOOL "" FORCE)

add_subdirectory(external/glfw)
target_link_libraries(${PROJECT_NAME} PUBLIC glfw)

add_subdirectory(external/glad)
target_link_libraries(${PROJECT_NAME} PUBLIC glad)

target_include_directories(${PROJECT_NAME} PUBLIC headers/)
