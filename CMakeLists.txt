cmake_minimum_required(VERSION 3.10)
project(boost_http)

set(CMAKE_CXX_STANDARD 11)

find_package(Boost COMPONENTS system filesystem REQUIRED)
find_package(Threads)

if (Boost_FOUND)

    message(STATUS "Boost_INCLUDE_DIRS: ${Boost_INCLUDE_DIRS}")
    message(STATUS "Boost_LIBRARIES: ${Boost_LIBRARIES}")
    message(STATUS "Boost_VERSION: ${Boost_VERSION}")

    include_directories(${Boost_INCLUDE_DIRS})
else ()
    message(FATAL_ERROR "Boost libraries not found")
endif ()

file(GLOB HEADERS "*.hpp")
file(GLOB SOURCES "*.cpp")

add_executable(boost_http ${SOURCES} ${HEADERS})

target_link_libraries(boost_http ${Boost_LIBRARIES})
target_link_libraries(boost_http ${CMAKE_THREAD_LIBS_INIT})
