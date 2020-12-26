cmake_minimum_required(VERSION 3.0)

project(gravitation)

set(CMAKE_CXX_STANDARD 20)

find_package(SFML 2.5 REQUIRED audio graphics window system)

if (SFML_FOUND)
    include_directories(${SFML_INCLUDE_DIR})
else ()
    message(ERROR_FATAL "Can not find SFML")
endif ()

add_executable(gravitation gravitation.cpp utils.cpp utils.hpp)

target_link_libraries(gravitation
        ${SFML_LIBRARIES}
        ${SFML_DEPENDENCIES}
        sfml-graphics
        sfml-window
        sfml-system
        m)