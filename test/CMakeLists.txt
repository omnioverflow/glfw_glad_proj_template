# Download GoogleTest as an external project
include (${PROJECT_SOURCE_DIR}/cmake/download_gtest.cmake)

project (RunUnitTests)

set (SOURCE_FILES test_foobar.cc)
add_executable (${PROJECT_NAME} main.cc ${SOURCE_FILES})

# Get the Engine include directories
get_target_property (
    MAIN_LIBRARY_INCLUDES FooBarEngine
    INCLUDE_DIRECTORIES
    )

target_include_directories (
    ${PROJECT_NAME} 
    PUBLIC ${MAIN_LIBRARY_INCLUDES}
    )
    
target_link_libraries (${PROJECT_NAME} ${CMAKE_PROJECT_NAME} gtest)

# Uncomment the following, if test resources are needed
# configure_file (
#    ${CMAKE_CURRENT_SOURCE_DIR}/resources/simple.json 
#    ${CMAKE_CURRENT_BINARY_DIR}/resources/simple.json COPYONLY
# )
