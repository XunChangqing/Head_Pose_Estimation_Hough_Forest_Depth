cmake_minimum_required(VERSION 2.6)

SET( 	HEAD_DEMO
		CRForestEstimator.cpp
		CRTree.cpp
		main.cpp 
)

SET(CMAKE_BUILD_TYPE "Release")

#modify according to your opencv installation
#SET( OPENCV_INCLUDES C:\gitwork\opencv249\build\include) 
#SET( OPENCV_LIBC C:\gitwork\opencv249\build\x86\vc11\lib) 

SET(OpenCV_DIR "C:\\gitwork\\opencv249\\build")
FIND_PACKAGE(OpenCV REQUIRED NO_CMAKE_BUILDS)

#INCLUDE_DIRECTORIES( . ${OPENCV_INCLUDES} )
#LINK_DIRECTORIES( ${OPENCV_LIB} )
INCLUDE_DIRECTORIES( . ${OpenCV_INCLUDE_DIRS} )
LINK_DIRECTORIES( ${OpenCV_LIB_DIR} )

add_executable( head_pose_estimation ${HEAD_DEMO})

target_link_libraries (head_pose_estimation opencv_core opencv_highgui opencv_imgproc )




