cmake_minimum_required(VERSION 3.16)

# Brookesia core and SquareLine demo are vendored under components/ so the
# project is self-contained.
set(EXTRA_COMPONENT_DIRS
    "${CMAKE_CURRENT_LIST_DIR}/components/brookesia_core"
    "${CMAKE_CURRENT_LIST_DIR}/components/brookesia_app_squareline_demo"
)

get_filename_component(REPOSITORY_ROOT "${CMAKE_CURRENT_LIST_DIR}" ABSOLUTE)
file(TO_CMAKE_PATH "${REPOSITORY_ROOT}" REPOSITORY_ROOT)
add_compile_options(
    "-ffile-prefix-map=${REPOSITORY_ROOT}=."
    "-fmacro-prefix-map=${REPOSITORY_ROOT}=."
)

include($ENV{IDF_PATH}/tools/cmake/project.cmake)
project(esp32-s3-touch-lcd-4-3c-brookesia)

# mcp-c-sdk 2.0.1 contains bounded strncpy calls that GCC 14 cannot prove are
# terminated.  Keep the compatibility exception local to that managed target;
# project sources retain the normal warnings-as-errors policy.
if(TARGET __idf_espressif__mcp-c-sdk AND CMAKE_C_COMPILER_ID STREQUAL "GNU")
    target_compile_options(__idf_espressif__mcp-c-sdk PRIVATE
        -Wno-error=stringop-truncation
    )
endif()
