cmake_minimum_required(VERSION 3.31.0)
project(planning)
set(CMAKE_CXX_STANDARD 17)

# 动态库和exe文件都指定到bin目录下面（变量和目录设置）
# linux中动态库用CMAKE_LIBRARY_OUTPUT_DIRECTORY 静态库用CMAKE_ARCHIVE_OUTPUT_DIRECTORY
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)

# 生成动态库
aux_source_directory(${PROJECT_SOURCE_DIR}/src SRC_LISTS)
add_library(common
SHARED
    ${SRC_LISTS}
)
# 包含所需要头文件
target_include_directories(common
PUBLIC
    ${PROJECT_SOURCE_DIR}/include
)

# 可执行文件
add_executable(planning_main planning_main.cpp)
# 包含所需要头文件
target_include_directories(planning_main
PUBLIC
    ${PROJECT_SOURCE_DIR}/include
)

# 链接动态库
target_link_libraries(planning_main
PUBLIC
common
)