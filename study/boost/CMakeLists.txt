cmake_minimum_required(VERSION 3.5)
project (use_boost)

# find a boost install with the libraries filesystem and system
find_package(Boost 1.46.1 REQUIRED COMPONENTS filesystem system)

# check if boost was found
if(Boost_FOUND)
    message ("boost found")
else()
    message (FATAL_ERROR "Cannot find Boost")
endif()

# Add an executable
add_executable(test main.cpp)

# link against the boost libraries
target_link_libraries( test
    PRIVATE
        Boost::filesystem
)  # Boost::filesystem相当于${Boost_FILESYSTEM_LIBRARY}
