cmake_minimum_required(VERSION 3.5)
project(helo_world)

# make后，在build文件夹下，创建共享库文件：libhello_library.so
add_library(hello_library SHARED
    src/hello.cpp
)

# 设置共享库要用到的头文件路径
target_include_directories(hello_library
    PUBLIC 
        ${PROJECT_SOURCE_DIR}/include
)

# Add an executable with the above sources
add_executable(hello_binary
    src/main.cpp
)

# link the new hello_library target with the hello_binary target
target_link_libraries( hello_binary
    PRIVATE 
        hello_library
)

############################################################
# Install
############################################################

# Binaries
# 将可执行文件hello_binary安装到${CMAKE_INSTALL_PREFIX}/bin 目录
install (TARGETS hello_binary
    DESTINATION bin)

# Library
# Note: may not work on windows
# 将库文件hello_library安装到${CMAKE_INSTALL_PREFIX}/lib 目录
install (TARGETS hello_library
    LIBRARY DESTINATION lib)

# Header files
# 将头文件安装到${CMAKE_INSTALL_PREFIX}/include 目录
install(DIRECTORY ${PROJECT_SOURCE_DIR}/include/ 
    DESTINATION include)

# Config
# 将配置文件cmake-examples.conf安装到${CMAKE_INSTALL_PREFIX}/etc 目录
install (FILES cmake-examples.conf
    DESTINATION etc)
