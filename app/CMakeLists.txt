cmake_minimum_required(VERSION 3.4.1)

set(distribution_DIR ${CMAKE_SOURCE_DIR}/../distribution)
set(pathToDlib ${CMAKE_SOURCE_DIR}/src/main/dlib)

include(${pathToDlib}/dlib/cmake)

add_library(native-my SHARED src/main/cpp/native-test.cpp)
set_target_properties(native-my PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${distribution_DIR}/libs/${ANDROID_ABI})

target_link_libraries(native-my dlib::dlib log)

SET(CMAKE_BUILE_TYPE "RELEASE")
SET(CMAKE_CXX_FLAGS_RELEASE "$ENV{CXXFLAGS} -O3 -Wall")
SET(CMAKE_BUILE_TYPE "DEBUG")
SET(CMAKE_CXX_FLAGS_DEBUG "-g -Wall")
