# I by accidentally deleted the original CMakeLists so this is v2
# To set up for the first time you do 
# cd build
# cmake ..
# Then whenever you make changes in the build dir do 
# cmake --build .

# This sets the CMAKE version
cmake_minimum_required(VERSION 3.10)

# This creates the project and also sets the PROJECT_NAME variable to the first param
project(MyProject VERSION 1.0)

# This sets the specified C++ version
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED TRUE)

# This is because I like using Neovim and without these it will say missing file even though
# I use NvChad with clangd, the compile_commands.json makes it so it recognizes the path
# The file is included as described below
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# This creates a variable called SOURCES which basically contains all the cpp files in src
file(GLOB SOURCES "${PROJECT_SOURCE_DIR}/src/*.cpp")

# This creates the executable file
add_executable(${PROJECT_NAME} ${SOURCES})

# include_directories adds paths to globally, so to all projects
# target_directories adds paths to a specified project
# Its so we don't need to use relative paths when doing like #include "../../....."
target_include_directories(${PROJECT_NAME} PUBLIC "${PROJECT_SOURCE_DIR}/include")

