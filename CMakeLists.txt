cmake_minimum_required(VERSION 3.21)
project(nprj)

set(CMAKE_CXX_STANDARD 17)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${PROJECT_SOURCE_DIR}/cmake")

aux_source_directory(. SRC_LIST)
add_executable(${PROJECT_NAME} ${SRC_LIST})

target_include_directories(${PROJECT_NAME} PRIVATE include)
target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_17)
target_compile_definitions(${PROJECT_NAME} PRIVATE IMGDIR="../assets/img/")

#target_include_directories(${PROJECT_NAME} PRIVATE ${SDL2_INCLUDE_DIRS})

find_package(SDL2 REQUIRED)
find_package(SDL2_image REQUIRED)
#find_package(SDL2_ttf REQUIRED)

#include_directories(${SDL2_INCLUDE_DIR}
#        ${SDL2_IMAGE_INCLUDE_DIR}
#        ${SDL2_TTF_INCLUDE_DIR})
#target_link_libraries(target ${SDL2_LIBRARY}
#        ${SDL2_IMAGE_LIBRARIES}
#        ${SDL2_TTF_LIBRARIES})

target_include_directories(${PROJECT_NAME} PRIVATE ${SDL2_INCLUDE_DIR}
                                                    ${SDL2_IMAGE_INCLUDE_DIR}})

target_link_libraries(${PROJECT_NAME} PRIVATE ${SDL2_LIBRARY}
        ${SDL2_IMAGE_LIBRARIES})

#find_package(SDL2_image REQUIRED)
#target_link_libraries(${PROJECT_NAME} SDL2::Image)
