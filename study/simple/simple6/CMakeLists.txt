cmake_minimum_required(VERSION 3.5)
project(hello_world)

# set a project version
# 最终生成的完整版本号字符串为 deb_example_VERSION=0.2.2
set (deb_example_VERSION_MAJOR 0)   # 将主版本号设置为0
set (deb_example_VERSION_MINOR 2)   # 将次版本号设置为2
set (deb_example_VERSION_PATCH 2)   # 将修订版本号设置为2
set (deb_example_VERSION "${deb_example_VERSION_MAJOR}.${deb_example_VERSION_MINOR}.${deb_example_VERSION_PATCH}")

#Generate the shared library from the library sources
add_library(hello_library SHARED src/hello.cpp)

target_include_directories(hello_library
    PUBLIC
        ${PROJECT_SOURCE_DIR}/include
)

# Add an executable with the above sources
add_executable(hello_binary src/main.cpp)

# link the new hello_library target with the hello_binary target
target_link_libraries( hello_binary
    PUBLIC
        hello_library
)

############################################################
# Install
############################################################

# Binaries
install (TARGETS hello_binary
    DESTINATION bin)

# Library
# Note: may not work on windows
install (TARGETS hello_library
    LIBRARY DESTINATION lib)

# Config
install (FILES cmake-examples.conf
    DESTINATION etc)

############################################################
# Create DEB
############################################################

# Tell CPack to generate a .deb package
set(CPACK_GENERATOR "DEB")

# Set a Package Maintainer.
# This is required
set(CPACK_DEBIAN_PACKAGE_MAINTAINER "Niu0217")

# Set a Package Version
set(CPACK_PACKAGE_VERSION ${deb_example_VERSION})

# Include CPack
include(CPack)

