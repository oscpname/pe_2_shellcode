cmake_minimum_required (VERSION 3.0)
project (injector)

set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} /MT")

set (srcs
	main.cpp
	util.cpp
)

set (hdrs
	util.h
)

add_executable ( ${PROJECT_NAME} ${hdrs} ${srcs})

if(PE2SHC_BUILD_TESTING)
	INSTALL( TARGETS ${PROJECT_NAME} DESTINATION ${CMAKE_INSTALL_PREFIX} COMPONENT ${PROJECT_NAME} )
endif()
