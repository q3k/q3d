cmake_minimum_required(VERSION 2.8)

project(q3d)

set(Q3D_HEADER_DIR ${CMAKE_CURRENT_BINARY_DIR})
set(Q3D_SCHEMA ${CMAKE_CURRENT_SOURCE_DIR}/object.fbs)
set(Q3D_HEADER ${Q3D_HEADER_DIR}/object_generated.h)

add_custom_command(
    OUTPUT ${Q3D_HEADER}
    COMMAND $<TARGET_FILE:flatc> --cpp --no-includes -o ${Q3D_HEADER_DIR}
            ${Q3D_SCHEMA}
    DEPENDS flatc)

add_custom_target(q3d_header DEPENDS ${Q3D_HEADER})
