cmake_minimum_required(VERSION 3.31.0)

project(planning)

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
aux_source_directory(. SRC_LISTS)
add_executable(planning_main ${SRC_LISTS})

