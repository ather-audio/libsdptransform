cmake_minimum_required(VERSION 3.28)

project(sdptransform VERSION 1.2.10)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

option(SDPTRANSFORM_BUILD_TEST_AND_README "Build test and readme-helper subdirs" OFF)
if(SDPTRANSFORM_BUILD_TEST_AND_README)
	subdirs(test readme-helper)
endif()

set(
	SOURCE_FILES
	src/grammar.cpp
	src/parser.cpp
	src/writer.cpp
)

set(
	HEADER_FILES
	include/sdptransform.hpp
)

add_library(sdptransform STATIC ${SOURCE_FILES} ${HEADER_FILES})

target_include_directories(sdptransform PUBLIC ${sdptransform_SOURCE_DIR}/include)

install(TARGETS sdptransform DESTINATION lib)
install(FILES ${HEADER_FILES} DESTINATION include/sdptransform)
