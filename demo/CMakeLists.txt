cmake_minimum_required(VERSION 2.6)

SET( 	HEAD_DEMO
		../CRForestEstimator.cpp
		../CRTree.cpp
		gl_camera.cpp
		main.cpp 
)

SET(CMAKE_BUILD_TYPE "Release")

SET(OpenCV_DIR "C:\\gitwork\\opencv249\\build")
FIND_PACKAGE(OpenCV REQUIRED NO_CMAKE_BUILDS_PATH)
IF(WIN32)

	#SET( OPENCV_INCLUDES C:\\gitwork\\DepthAlgorithm\\Third\\opencv248\\build-vs9\\install\\include) 
	#SET( OPENCV_LIB C:\\gitwork\\DepthAlgorithm\\Third\\opencv248\\build-vs9\\install\\x86\\vc9\\lib) 

	SET( OPENNI_INCLUDES "C:\\Program Files (x86)\\OpenNI\\Include") 
	SET( OPENNI_LIB "C:\\Program Files (x86)\\OpenNI\\Lib") 

	SET( FREEGLUT_LIB C:\\gitwork\\freeglut\\lib) 
	LINK_DIRECTORIES( ${OPENNI_LIB} ${FREEGLUT_LIB} )


ELSE(WIN32)

	SET( OPENCV_INCLUDES /include ) 
	SET( OPENCV_LIB /lib ) 
	SET( OPENNI_INCLUDES /home/biwi/gfanelli/OpenNI/Include ) 
	SET( OPENNI_LIB /home/biwi/gfanelli/OpenNI/Platform/Linux86/Bin/Release ) 

	#assuming freeglut installed on linux
	LINK_DIRECTORIES( ${OPENNI_LIB} ${OpenCV_LIB_DIR} )

ENDIF(WIN32)
	
INCLUDE_DIRECTORIES( . .. ${OPENNI_INCLUDES} )

	
add_executable( head_pose_estimation_demo ${HEAD_DEMO})


IF(WIN32)
target_link_libraries (head_pose_estimation_demo opencv_core opencv_highgui opencv_imgproc OpenNI freeglut)
ELSE(WIN32)
target_link_libraries (head_pose_estimation_demo opencv_core opencv_highgui opencv_imgproc OpenNI GLU glut)
ENDIF(WIN32)

