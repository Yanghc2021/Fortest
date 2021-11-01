cmake_minimum_required(VERSION 3.5.1)
project(Untitled1)

if(NOT TARGET Kanzi::kzappfw)
    find_package(Kanzi REQUIRED CONFIG CMAKE_FIND_ROOT_PATH_BOTH)
endif()

include(kanzi-common)

add_executable(Untitled1 src/untitled1.cpp)

if(ANDROID)
    target_link_libraries(Untitled1 -Wl,--whole-archive Kanzi::kzappfw -Wl,--no-whole-archive)
else()
    target_link_libraries(Untitled1 Kanzi::kzappfw)
endif()

target_link_libraries(Untitled1 Kanzi::kzui Kanzi::kzcoreui Kanzi::kzjs)

set_target_properties(Untitled1 PROPERTIES VS_DEBUGGER_WORKING_DIRECTORY "${PROJECT_SOURCE_DIR}/bin")
