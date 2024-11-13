cmake_minimum_required(VERSION 3.16)
project(SmartHomeController)
set(CMAKE_CXX_STANDARD 11)
find_package(Qt6 REQUIRED COMPONENTS Core Quick)
add_subdirectory(src)
set(QML_IMPORT_PATH ${CMAKE_CURRENT_SOURCE_DIR}/qml)
add_executable(SmartHomeController main.cpp)
target_link_libraries(SmartHomeController PRIVATE Qt6::Core Qt6::Quick)

