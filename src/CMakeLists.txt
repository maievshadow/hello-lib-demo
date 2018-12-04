cmake_minimum_required (VERSION 2.6) 
add_library(hello SHARED ${PROJECT_SOURCE_DIR}/src/hello.c) 
add_library(hello_static STATIC ${PROJECT_SOURCE_DIR}/src/hello.c) 

SET_TARGET_PROPERTIES (hello_static PROPERTIES OUTPUT_NAME "hello")
GET_TARGET_PROPERTY (OUTPUT_VALUE hello_static OUTPUT_NAME)

MESSAGE (STATUS "This is the hello_static OUTPUT_NAME: " ${OUTPUT_VALUE})

SET_TARGET_PROPERTIES (hello_static PROPERTIES CLEAN_DIRECT_OUTPUT 1)
SET_TARGET_PROPERTIES (hello PROPERTIES CLEAN_DIRECT_OUTPUT 1)
SET_TARGET_PROPERTIES (hello PROPERTIES VERSION 1.2 SOVERSION 1)

SET(CMAKE_CXX_FLAGS_DEBUG "$ENV{CXXFLAGS} -O0 -Wall -g -ggdb") # Debug模式下的编译指令 
#SET(CMAKE_CXX_FLAGS_RELEASE "$ENV{CXXFLAGS} -O3 -Wall") # Release模式下的编译指令
#install(TARGETS hello LIBRARY DESTINATION lib)

#SET(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/../bin)       #设置可执行文件的输出目录 
#set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_DEBUG ${PROJECT_SOURCE_DIR}/bin)   
#set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_RELEASE ${PROJECT_SOURCE_DIR}/../bin)
#上面两条语句分别设置了Debug版本和Release版本可执行文件的输出目录,
#一旦设置上面的属性,在任何环境下生成的可执行文件都将直接放在你所设置的目录

SET(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)           #设置库文件的输出目录 
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY_DEBUG ${PROJECT_SOURCE_DIR}/lib)    
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY_RELEASE ${PROJECT_SOURCE_DIR}/lib) 
#上面两条语句分别设置了Debug版本和Release版本库文件的输出目录, 
#一旦设置上面的属性,在任何环境下生成的库文件都将直接放在你所设置的目录.


INSTALL (TARGETS hello hello_static LIBRARY DESTINATION lib

ARCHIVE DESTINATION lib)

INSTALL (FILES hello.h DESTINATION include/hello)

#INSTALL (FILES hello.h DESTINATION {PROJECT_SOURCE_DIR}/include/hello)