cmake_minimum_required(VERSION 3.28)
project(PrettyMuchNothing LANGUAGES CXX)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

include(FetchContent)
FetchContent_Declare(SFML
    GIT_REPOSITORY https://github.com/SFML/SFML.git
    GIT_TAG 3.0.2
    GIT_SHALLOW ON
    EXCLUDE_FROM_ALL
    SYSTEM)
FetchContent_MakeAvailable(SFML)

set(SOURCE_PATH "${PROJECT_SOURCE_DIR}/src")
set(INCLUDE_PATH "${PROJECT_SOURCE_DIR}/include")

set(SOURCE_FILES
    ${SOURCE_PATH}/main.cpp
    ${SOURCE_PATH}/Game.cpp
    ${SOURCE_PATH}/Menu.cpp
)

set(HEADER_FILES
    ${INCLUDE_PATH}/Game.h
    ${INCLUDE_PATH}/Menu.h
)


add_executable(PrettyMuchNothing ${SOURCE_FILES} ${HEADER_FILES})

target_compile_features(PrettyMuchNothing PRIVATE cxx_std_17)
target_link_libraries(PrettyMuchNothing PRIVATE SFML::Graphics SFML::System SFML::Audio SFML::Window SFML::Network)