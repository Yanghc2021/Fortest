cmake_minimum_required(VERSION 3.5.1)
project(mycar_Vehicle)

if(NOT TARGET Kanzi::kzappfw)
    find_package(Kanzi REQUIRED CONFIG CMAKE_FIND_ROOT_PATH_BOTH)
endif()

include(kanzi-common)

add_executable(mycar_Vehicle src/mycar_vehicle.cpp)

if(ANDROID)
    target_link_libraries(mycar_Vehicle -Wl,--whole-archive Kanzi::kzappfw -Wl,--no-whole-archive)
else()
    target_link_libraries(mycar_Vehicle Kanzi::kzappfw)
endif()

target_link_libraries(mycar_Vehicle Kanzi::kzui Kanzi::kzcoreui Kanzi::kzjs)

set_target_properties(mycar_Vehicle PROPERTIES VS_DEBUGGER_WORKING_DIRECTORY "${PROJECT_SOURCE_DIR}/bin")
