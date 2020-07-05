cmake_minimum_required(VERSION 2.8)
project( yolo_mark CXX )

find_package(PkgConfig)
pkg_check_modules(OPENCV3 REQUIRED opencv3)

set(OPENCV_INCLUDES "${OPENCV3_INCLUDE_DIRS}")
set(OPENCV_LIBPATH "${OPENCV3_LIBRARY_DIRS}")
set(OPENCV_LIBS "${OPENCV3_LIBRARIES}")

set( sources main.cpp )

include_directories(${OPENCV_INCLUDES})

link_directories(${OPENCV_LIBPATH})

add_executable( yolo_mark ${sources} )

target_compile_options( yolo_mark PUBLIC -std=c++11 -fpermissive -w -Wall )

target_link_libraries( yolo_mark ${OPENCV_LIBS} -L/usr/lib64 -ldl )
