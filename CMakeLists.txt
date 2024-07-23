cmake_minimum_required(VERSION 3.16)
project(toring LANGUAGES CXX)

if (NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Release)
endif()

set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_STANDARD 11)

file(GLOB SOURCE_FILES "src/*.cpp")
file(GLOB HEADER_FILES "include/*.h")

add_library(${PROJECT_NAME} SHARED ${SOURCE_FILES})

# setting library properties
set_target_properties(${PROJECT_NAME} PROPERTIES
    VERSION 0.0.1
    # SOVERSION ${PROJECT_VERSION_MAJOR}
)

# including project files
include_directories(.)

# install library
install(TARGETS ${PROJECT_NAME} DESTINATION lib/${PROJECT_NAME})

# install header files
install(FILES ${HEADER_FILES} DESTINATION include/${PROJECT_NAME})
