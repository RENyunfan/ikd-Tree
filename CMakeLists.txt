cmake_minimum_required(VERSION 2.8 FATAL_ERROR)

project(ikd_tree_demo)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_BUILD_TYPE Release)
set(CMAKE_CXX_FLAGS "-O3 -Wall")
#set(CMAKE_BUILD_TYPE Debug)
#set(CMAKE_CXX_FLAGS "-O -Wall -g")

find_package(PCL REQUIRED)

include_directories(
        ${PCL_INCLUDE_DIRS}
        ikd-Tree
)

add_library(ikd_tree
        ikd-Tree/ikd_Tree.cpp
)
target_link_libraries(ikd_tree PUBLIC
        ${PCL_LIBRARIES}
        pthread
)

add_executable(ikd_tree_demo examples/ikd_Tree_demo.cpp)
target_link_libraries(ikd_tree_demo ikd_tree)

add_executable(ikd_tree_async_demo examples/ikd_Tree_Async_demo.cpp)
target_link_libraries(ikd_tree_async_demo
        ikd_tree
)
#
#add_executable(ikd_tree_Search_demo examples/ikd_Tree_Search_demo.cpp ikd-Tree/ikd_Tree.cpp)
#target_link_libraries(ikd_tree_Search_demo ${PCL_LIBRARIES})