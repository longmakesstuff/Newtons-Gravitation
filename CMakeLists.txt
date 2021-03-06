cmake_minimum_required(VERSION 3.0)

project(gravitation)

set(CMAKE_CXX_STANDARD 20)

find_package(SFML 2.5 REQUIRED audio graphics window system)

if (SFML_FOUND)
    include_directories(${SFML_INCLUDE_DIR})
else ()
    message(ERROR_FATAL "Can not find SFML")
endif ()

add_executable(gravitation main.cpp Planet.hpp Planet.cpp Universe.hpp Universe.cpp Utils.cpp Utils.hpp SizedVector.hpp)

target_link_libraries(gravitation
        ${SFML_LIBRARIES}
        ${SFML_DEPENDENCIES}
        sfml-graphics
        sfml-window
        sfml-system
        m)


file(GLOB resource_files "${CMAKE_CURRENT_SOURCE_DIR}/data/*")
foreach (item ${resource_files})
    FILE(COPY ${item} DESTINATION "${CMAKE_BINARY_DIR}")
endforeach ()