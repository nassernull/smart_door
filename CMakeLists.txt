cmake_minimum_required(VERSION 2.8)
CMAKE_POLICY(SET CMP0012 NEW)
PROJECT(Smart_Door)
FIND_PACKAGE(OpenCV 4.4.0 REQUIRED)
MESSAGE("OpenCV Version: ${OpenCV_VERSION}")
INCLUDE_DIRECTORIES(${OpenCV_INCLUDE_DIR})
LINK_DIRECTORIES(${OpenCV_LINK_DIR})

#Starting from here define your own library
INCLUDE_DIRECTORIES(${PROJECT_SOURCE_DIR}/include)
INCLUDE_DIRECTORIES(/usr/include/opencv4)
LINK_DIRECTORIES(/usr/local/lib)
ADD_SUBDIRECTORY(src)
MESSAGE("OpenCV LINK DIR: " ${OpenCV_LINK_DIR})
MESSAGE("OpenCV LIBS: " ${OpenCV_LIBS})
set(EXTRA_LIBS ${EXTRA_LIBS} faceDetection faceRecognition wiringPi wiringPiDev SocketServer NasserSockets pthread  ${OpenCV_LIBS})


SET(MAIN main.cpp)
ADD_EXECUTABLE(${PROJECT_NAME} ${MAIN})
TARGET_LINK_LIBRARIES(${PROJECT_NAME} ${EXTRA_LIBS})


