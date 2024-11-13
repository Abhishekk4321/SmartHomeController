# src/CMakeLists.txt

# Use GLOB_RECURSE to recursively gather all .cpp and .h files
file(GLOB_RECURSE SRC_FILES *.cpp *.h)

# Create a library from the collected source files
add_library(SmartHomeLib ${SRC_FILES})

# Link necessary Qt libraries to this library
target_link_libraries(SmartHomeLib PRIVATE Qt${QT_VERSION_MAJOR}::Core Qt${QT_VERSION_MAJOR}::Quick)

# Ensure the library follows C++17 standards
set_target_properties(SmartHomeLib PROPERTIES
    CXX_STANDARD 17
    CXX_STANDARD_REQUIRED ON
)
