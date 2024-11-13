cmake_minimum_required(VERSION 3.16)
set(RESOURCE_FILES qml/resources.qrc)
project(SmartHomeController VERSION 0.1 LANGUAGES CXX)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Find required Qt components including Widgets
find_package(QT NAMES Qt6 Qt5 REQUIRED COMPONENTS Core Quick Qml Widgets)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Core Quick Qml Widgets)

add_subdirectory(src)

# Include all QML files from the qml directory
set(QML_IMPORT_PATH ${CMAKE_CURRENT_SOURCE_DIR}/qml)

# Define executable with main.cpp located in the src directory
add_executable(SmartHomeController src/main.cpp)

# Link necessary Qt libraries including Widgets
target_link_libraries(SmartHomeController PRIVATE Qt${QT_VERSION_MAJOR}::Core Qt${QT_VERSION_MAJOR}::Quick Qt${QT_VERSION_MAJOR}::Qml Qt${QT_VERSION_MAJOR}::Widgets)
# Include the resource file


# Set path to QML directory for deployment if needed
set_target_properties(SmartHomeController PROPERTIES
    QT_QML_IMPORT_PATH "${CMAKE_CURRENT_SOURCE_DIR}/qml"
    QT_QML_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/qml"
)
# Link SmartHomeLib to the main executable
#target_link_libraries(SmartHomeController PRIVATE SmartHomeLib)
