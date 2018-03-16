project(QtAdvancedDockingSystem)
cmake_minimum_required(VERSION 3.0)

add_definitions(-DADS_EXPORT)

find_package(Qt5 COMPONENTS Core Gui Widgets REQUIRED)

set(CMAKE_CXX_FLAGS ${CMAKE_CXX_FLAGS} -pedantic)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

file(GLOB SOURCES AdvancedDockingSystem/src/*.cpp)
file(GLOB HEADERS AdvancedDockingSystem/include/ads/*.h)

add_library(QtAdvancedDockingSystem SHARED ${SOURCES} ${HEADERS} AdvancedDockingSystem/res/ads.qrc)

target_include_directories(QtAdvancedDockingSystem PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/AdvancedDockingSystem/include>
        $<INSTALL_INTERFACE:${INSTALL_CMAKE_DIR}/public>)

target_link_libraries(QtAdvancedDockingSystem Qt5::Gui Qt5::Widgets Qt5::Core)