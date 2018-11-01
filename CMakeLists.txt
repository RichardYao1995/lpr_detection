cmake_minimum_required(VERSION 3.6)
project(lpr)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR})
find_package(OpenCV 3.3.1 REQUIRED)
include_directories( ${OpenCV_INCLUDE_DIRS})
include_directories(include)

set(SRC_DETECTION src/PlateDetection.cpp  src/util.h include/PlateDetection.h)

set(SRC_FINEMAPPING src/FineMapping.cpp )

set(SRC_FASTDESKEW src/FastDeskew.cpp )

set(SRC_SEGMENTATION src/PlateSegmentation.cpp )

set(SRC_RECOGNIZE src/Recognizer.cpp src/CNNRecognizer.cpp)

set(SRC_PIPLINE src/Pipeline.cpp)

set(SRC_SEGMENTATIONFREE src/SegmentationFreeRecognizer.cpp )

#TEST
add_executable(MAIN ${SRC_DETECTION} ${SRC_FINEMAPPING} ${SRC_FASTDESKEW} ${SRC_SEGMENTATION} ${SRC_RECOGNIZE} ${SRC_PIPLINE} ${SRC_SEGMENTATIONFREE} main.cpp)
target_link_libraries(MAIN ${OpenCV_LIBS})
