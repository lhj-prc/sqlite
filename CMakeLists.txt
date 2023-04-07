cmake_minimum_required(VERSION 3.18)
project(sqlite)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_FLAGS "-g -rdynamic")
set(EXECUTABLE_OUTPUT_PATH  ${CMAKE_CURRENT_SOURCE_DIR}/bin)

include_directories(include)
aux_source_directory(source SOURCE)
add_library(sqlite STATIC ${SOURCE})
target_link_libraries(sqlite pthread)
target_link_libraries(sqlite dl)

add_executable(testdb main.c)
target_link_libraries(testdb sqlite)
