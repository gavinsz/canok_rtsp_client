cmake_minimum_required(VERSION 2.8.0 FATAL_ERROR)
PROJECT(rtsp_client)
set(APP_NAME rtsp_client)

add_compile_options( -O2 -g -std=c++11)

#保存pcm文件到flash中
#add_compile_options(-DSAVED_PCM_TO_FLASH)

set(CMAKE_VERBOSE_MAKEFILE ON)


set(SOURCE
	cH264RTP.cpp
	com_debug.cpp
	com_net.cpp
	com_queue.cpp
	cRTPClient.cpp
	cRTPParse.cpp
	cRTSPClient.cpp
	cRTSPprotocol.cpp
	memwatch.cpp
	Pcapfile.cpp
	test_main.cpp
)

include_directories(
	./
)

set(APP_DEPENDENT_LIBS
	-lrt -pthread -lpthread -ldl -lm
)

ADD_EXECUTABLE(${APP_NAME} ${SOURCE})
target_link_libraries(${APP_NAME} ${APP_DEPENDENT_LIBS})

install(TARGETS ${APP_NAME} DESTINATION bin)