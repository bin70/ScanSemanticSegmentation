cmake_minimum_required(VERSION 3.5.1)
project(scan_labeling)

SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14")
SET(CMAKE_BUILD_TYPE Debug)
SET(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin) 

find_package(Eigen3 REQUIRED)
include_directories(${EIGEN3_INCLUDE_DIR})

set(PCL_DIR $ENV{HOME}/pcl_1_8_1/share/pcl-1.8)
find_package(PCL 1.8 REQUIRED)
add_definitions(${PCL_DEFINITIONS})
include_directories(${PCL_INCLUDE_DIRS})

include_directories(${PROJECT_SOURCE_DIR}/include
    ${PROJECT_SOURCE_DIR}/../Toolkit/include)

add_executable(scanLabeling src/ScanLabeling.cpp)
target_link_libraries(scanLabeling ${PCL_LIBRARIES})

add_executable(simDegradation src/SimDegradation.cpp)
target_link_libraries(simDegradation ${PCL_LIBRARIES})

add_executable(addNoise src/AddNoiseToS3DIS.cpp)
target_link_libraries(addNoise ${PCL_LIBRARIES})