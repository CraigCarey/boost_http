cmake_minimum_required(VERSION 3.10)

project(boost_http)

set(CMAKE_CXX_STANDARD 11)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/bin")

# Gather all sources except the main entry point
file(GLOB_RECURSE INC_FILES src/*/*.hpp)
file(GLOB_RECURSE SRC_FILES src/*/*.cpp)

# Check dependencies
find_package(Boost COMPONENTS system filesystem unit_test_framework REQUIRED)
find_package(Threads)

# Unit tests
add_subdirectory(test)

# Assign the include directories
include_directories(${Boost_INCLUDE_DIRS})

# Build
set(SOURCE_FILES ${INC_FILES} ${SRC_FILES})
add_executable(boost_http src/main.cpp ${SOURCE_FILES})
target_link_libraries(boost_http ${Boost_LIBRARIES})
target_link_libraries(boost_http ${CMAKE_THREAD_LIBS_INIT})
