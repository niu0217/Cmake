cmake_minimum_required(VERSION 3.5)
project(hello_world)

############################################################
# Create a library
############################################################

#Generate the shared library from the library sources
add_library(hello_library SHARED 
    src/hello.cpp
)   #make后，在build文件夹下，创建共享库文件：libhello_library.so
add_library(hello::library ALIAS hello_library)  #为hello_library创建一个别名hello::library

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
        hello::library
)