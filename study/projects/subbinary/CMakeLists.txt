project(subbinary)

# Create the executable
# ${PROJECT_NAME}=subbinary
add_executable(${PROJECT_NAME} main.cpp)

# Link the static library from subproject1 using its alias sub::lib1
# Link the header only library from subproject2 using its alias sub::lib2
# This will cause the include directories for that target to be added to this project
target_link_libraries(${PROJECT_NAME}
    sub::lib1   # 链接sublibrary1项目库文件
    sub::lib2   # 链接sublibrary2项目库文件
)
