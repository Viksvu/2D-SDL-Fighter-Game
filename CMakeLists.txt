cmake_minimum_required(VERSION 3.10)
project(SpriteSheetAnimation)


set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)


find_package(SDL2 REQUIRED)
find_package(SDL2_image REQUIRED)


include_directories(${SDL2_INCLUDE_DIRS} ${SDL2_IMAGE_INCLUDE_DIRS})


set(SourceFiles main.cpp)


add_executable(${PROJECT_NAME} ${SourceFiles})


target_link_libraries(${PROJECT_NAME} ${SDL2_LIBRARIES} ${SDL2_IMAGE_LIBRARIES})


target_link_libraries(${PROJECT_NAME} SDL2 SDL2_image)

add_custom_command(TARGET ${PROJECT_NAME} POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_if_different
    ${CMAKE_SOURCE_DIR}/player1.png 
    $<TARGET_FILE_DIR:${PROJECT_NAME}>/player1.png)  



add_custom_command(TARGET ${PROJECT_NAME} POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_if_different
    ${CMAKE_SOURCE_DIR}/Demo.png 
    $<TARGET_FILE_DIR:${PROJECT_NAME}>/Demo.png)  
    
# Copy the PNG file to the build directory after the target is built
add_custom_command(TARGET ${PROJECT_NAME} POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_if_different
    ${CMAKE_SOURCE_DIR}/player2.png # Path to the source PNG file
    $<TARGET_FILE_DIR:${PROJECT_NAME}>/player2.png)  # Destination in the build directory
