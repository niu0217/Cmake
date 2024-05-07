# Set the project name
project (sublibrary2)

# ${PROJECT_NAME}=sublibrary2
add_library(${PROJECT_NAME} INTERFACE)   # 创建interface library
add_library(sub::lib2 ALIAS ${PROJECT_NAME})  # 创建别名sub::lib2指代库文件

target_include_directories(${PROJECT_NAME}
    INTERFACE
        ${PROJECT_SOURCE_DIR}/include
)
