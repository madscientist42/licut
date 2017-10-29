CMAKE_MINIMUM_REQUIRED (VERSION 2.8)
PROJECT (licut)

# Specify where we're dropping things- the end-user of this system
# can specify elsewhere, but we're going to pour it here to make
# it easier on us...
if(CMAKE_SOURCE_DIR STREQUAL CMAKE_BINARY_DIR)
    SET(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/build)
endif()

# Do our up-front config checks...
INCLUDE(GNUInstallDirs)

# Declare our project's additional include path entries...
INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR}/include
    ${CMAKE_CURRENT_BINARY_DIR}/include)

ADD_EXECUTABLE(licut main.cpp licut_svg.cpp licut_probe.cpp licut_io.cpp)
TARGET_LINK_LIBRARIES(licut gflags)

INSTALL(TARGETS licut DESTINATION ${CMAKE_INSTALL_BINDIR})
