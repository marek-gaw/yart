cmake_minimum_required (VERSION 3.2)
project (yart)


set (CMAKE_CXX_FLAGS "-Wall -Wextra -pedantic -std=c++11")
set(CMAKE_CXX_STANDARD 11)

set(CMAKE_MODULE_PATH /usr/local/lib/cmake)
set(CMAKE_MODULE_PATH /usr/local/lib/x86_64-linux-gnu/cmake/glm)
set(CMAKE_PREFIX_PATH /usr/local/lib/cmake/glfw)

find_package (OpenGL REQUIRED)
find_package (glfw3 REQUIRED)
find_package(glm CONFIG REQUIRED)
find_package (GLEW REQUIRED STATIC)
find_package(SDL2 REQUIRED)

include_directories(${GLEW_INCLUDE_DIRS} ${OPENGL_INCLUDE_DIRS} ${SDL2_INCLUDE_DIRS})
link_directories(${GLEW_LIBRARY_DIRS} ${OPENGL_LIBRARY_DIRS})
add_definitions(${GLEW_DEFINITIONS} ${OPENGL_DEFINITIONS})

file(GLOB_RECURSE SOURCES
        "${CMAKE_SOURCE_DIR}/src/*.cpp")
file(GLOB_RECURSE HEADERS
   "${CMAKE_SOURCE_DIR}/src/*.hpp")


add_executable(yart ${SOURCES} ${HEADERS})
target_link_libraries (yart ${OPENGL_LIBRARIES}
    SDL2main SDL2 SDL2_image
    ${GLEW_LIBRARY})


add_custom_target(Additional_files DEPENDS ALL SOURCES
      README.md
      )





