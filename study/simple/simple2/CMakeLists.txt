cmake_minimum_required(VERSION 3.5)
project (hello_headers)

# Create a sources variable with a link to all cpp files to compile
set(SOURCES
    src/hello.cpp
    src/main.cpp
)
# 通过GLOB来正则匹配src路径下的所有cpp文件
# file(GLOB SOURCES "src/*.cpp")

# Add an executable with the above sources
add_executable(hello ${SOURCES})

# Set the directories that should be included in the build command for this target
# when running g++ these will be included as -I/directory/path/
target_include_directories(hello
    PRIVATE 
        ${PROJECT_SOURCE_DIR}/include
)
