cmake_minimum_required(VERSION 2.8)

project(HELLO)

#aux_source_directory(. SRC_LIST)
include_directories(./include ./testFun)
set( SRC_LIST
    src/hello.c
    src/test_add.c
    src/test_add1.c
    testFun/test_fun.c
 )

set(LIB_LIST ${PROJECT_SOURCE_DIR}/testFun/test_fun.c)

add_library(testFunc_shared SHARED ${LIB_LIST})
add_library(testFunc_static STATIC ${LIB_LIST})

set_target_properties(testFunc_shared PROPERTIES OUTPUT_NAME "testFunc")
set_target_properties(testFunc_static PROPERTIES OUTPUT_NAME "testFunc")

set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

add_executable(hello2 ${SRC_LIST})

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)

