cmake_minimum_required (VERSION 2.6) 
add_library(hello SHARED ${PROJECT_SOURCE_DIR}/libhello/hello.c) 
install(TARGETS hello LIBRARY DESTINATION lib)
