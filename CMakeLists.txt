cmake_minimum_required(VERSION 3.10)
project(SpriteSheetAnimation)

# Set the C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Find SDL2 and SDL2_image packages
find_package(SDL2 REQUIRED)
find_package(SDL2_image REQUIRED)

# Include directories for SDL2 and SDL2_image
include_directories(${SDL2_INCLUDE_DIRS} ${SDL2_IMAGE_INCLUDE_DIRS})

# Source files
set(SourceFiles main.cpp)

# Add the executable target
add_executable(${PROJECT_NAME} ${SourceFiles})

# Link SDL2 and SDL2_image libraries
target_link_libraries(${PROJECT_NAME} ${SDL2_LIBRARIES} ${SDL2_IMAGE_LIBRARIES})

# In case SDL2_LIBRARIES and SDL2_IMAGE_LIBRARIES aren't set
target_link_libraries(${PROJECT_NAME} SDL2 SDL2_image)

# Copy the PNG file to the build directory after the target is built
add_custom_command(TARGET ${PROJECT_NAME} POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_if_different
    ${CMAKE_SOURCE_DIR}/player1.png # Path to the source PNG file
    $<TARGET_FILE_DIR:${PROJECT_NAME}>/player1.png)  # Destination in the build directory


# Copy the PNG file to the build directory after the target is built
add_custom_command(TARGET ${PROJECT_NAME} POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_if_different
    ${CMAKE_SOURCE_DIR}/Demo.png # Path to the source PNG file
    $<TARGET_FILE_DIR:${PROJECT_NAME}>/Demo.png)  # Destination in the build directory
    
# Copy the PNG file to the build directory after the target is built
add_custom_command(TARGET ${PROJECT_NAME} POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_if_different
    ${CMAKE_SOURCE_DIR}/player2.png # Path to the source PNG file
    $<TARGET_FILE_DIR:${PROJECT_NAME}>/player2.png)  # Destination in the build directory