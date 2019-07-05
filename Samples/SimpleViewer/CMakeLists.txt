cmake_minimum_required(VERSION 2.8)

project(bone)

set(OPENNI2_DIR "/home/cy8182/repos/OpenNI-Linux-x64-2.3")
set(NITE2_DIR "/home/cy8182/repos/NiTE-2.0.0")
set(NI_LIB_DIRNAME "Redist")

find_package(OpenCV REQUIRED)
find_package(OpenGL REQUIRED)
find_package(GLUT REQUIRED)

include_directories(
	${OPENNI2_DIR}/Include
    	${NITE2_DIR}/Include
	${OPENGL_INCLUDE_DIR}
	${GLUT_INCLUDE_DIR}
	${OPENCV_INCLUDE}
    	${CMAKE_CURRENT_SOURCE_DIR}
	)

link_directories(
	${OPENCV_LIB}
	${OPENNI2_DIR}/${NI_LIB_DIRNAME}
	${NITE2_DIR}/${NI_LIB_DIRNAME}
	)

add_executable(${PROJECT_NAME}
	main.cpp
	Viewer.cpp
)

target_link_libraries(${PROJECT_NAME}
	OpenNI2
	NiTE2
	${OPENGL_LIBRARIES}
	${GLUT_LIBRARIES}
	${OpenCV_LIBS}
)
