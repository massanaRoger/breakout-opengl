cmake_minimum_required(VERSION 3.10)

project(Breakout)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Add subdirectories for external libraries
add_subdirectory(vendor/glfw)
add_subdirectory(vendor/glad)
add_subdirectory(vendor/glm)

# Add executable
add_executable(Breakout src/main.cpp src/Game.cpp src/Texture.cpp src/ResourceManager.cpp src/Shader.cpp)

# Add include directories to the target
target_include_directories(Breakout PRIVATE ${PROJECT_SOURCE_DIR}/vendor/glfw/include)
target_include_directories(Breakout PRIVATE ${PROJECT_SOURCE_DIR}/vendor/glad/include)
target_include_directories(Breakout PRIVATE ${PROJECT_SOURCE_DIR}/vendor/glm)
target_include_directories(Breakout PRIVATE ${PROJECT_SOURCE_DIR}/vendor/stb)
target_include_directories(Breakout PRIVATE ${PROJECT_SOURCE_DIR}/src)

# Link external libraries to the executable
target_link_libraries(Breakout PRIVATE glad glfw glm)

# Enable generation of compile_commands.json
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

