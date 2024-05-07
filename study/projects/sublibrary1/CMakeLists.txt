# Set the project name
project (sublibrary1)

# Add a library with the above sources
# ${PROJECT_NAME}=sublibrary1
add_library(${PROJECT_NAME} src/sublib1.cpp)   # 利用src/sublib1.cpp生成库文件(默认为静态库)
add_library(sub::lib1 ALIAS ${PROJECT_NAME})   # 创建别名sub::lib1 指代静态库文件

target_include_directories( ${PROJECT_NAME}
    PUBLIC ${PROJECT_SOURCE_DIR}/include
)
