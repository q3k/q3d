cmake_minimum_required(VERSION 2.8)

project(q3d)

set(Q3D_HEADER_DIR ${CMAKE_CURRENT_BINARY_DIR})
set(Q3D_SCHEMA ${CMAKE_CURRENT_SOURCE_DIR}/q3d_object.fbs)
set(Q3D_HEADER ${Q3D_HEADER_DIR}/q3d_object_generated.h)

if(NOT FLATC)
    # If not specified explicitly, use flatc from an adjacent flatbuffers
    # CMake project.
    add_custom_command(
        OUTPUT ${Q3D_HEADER}
        COMMAND $<TARGET_FILE:flatc> --cpp --no-includes -o ${Q3D_HEADER_DIR}
                ${Q3D_SCHEMA}
        DEPENDS flatc)
else()
    add_custom_command(
        OUTPUT ${Q3D_HEADER}
        COMMAND ${FLATC} --cpp --no-includes -o ${Q3D_HEADER_DIR} ${Q3D_SCHEMA})
endif()

add_custom_target(q3d_header DEPENDS ${Q3D_HEADER})
