cmake_minimum_required(VERSION 3.10.2)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

project(missions_copter)

add_executable(missions_copter
    missions_copter.cpp
)

add_executable(missions_copter_test
    missions_copter_test.cpp
)

find_package(MAVSDK REQUIRED)

target_link_libraries(missions_copter
    MAVSDK::mavsdk
)

target_link_libraries(missions_copter_test
    MAVSDK::mavsdk
)

if(NOT MSVC)
    add_compile_options(missions_copter missions_copter_test PRIVATE -Wall -Wextra)
else()
    add_compile_options(missions_copter missions_copter_test PRIVATE -WX -W2)
endif()
