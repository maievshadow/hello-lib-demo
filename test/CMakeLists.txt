cmake_minimum_required (VERSION 2.6) 
link_libraries(${PROJECT_SOURCE_DIR}/lib)
#include_directories(${PROJECT_SOURCE_DIR}/include)
add_executable(Main
    main.c
)