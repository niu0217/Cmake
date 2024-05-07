# Set the minimum version of CMake that can be used
cmake_minimum_required(VERSION 3.5)    # 需要cmake最低版本为3.5

# Set the project name
project (hello_cmake)   # 设置此项目的名称为hello_cmake

# Add an executable
add_executable(hello main.cpp)    # 将main.cpp源文件，生成可执行文件hello
