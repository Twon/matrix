FetchContent_Declare(catch2 GIT_REPOSITORY https://github.com/catchorg/Catch2 GIT_TAG v3.5.3)
FetchContent_MakeAvailable(catch2)

add_executable(test-std-matrix)

target_sources(test-std-matrix
    PRIVATE
        matrix.tests.cpp
)

target_link_libraries(test-std-matrix
    PRIVATE
        std-matrix
        Catch2::Catch2WithMain
)

set_target_properties(test-std-matrix
    PROPERTIES
        CXX_STANDARD 23
        CXX_STANDARD_REQUIRED YES
        CXX_EXTENSIONS NO
        RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin
)

add_test(
    NAME test-std-matrix
    COMMAND test-std-matrix
    WORKING_DIRECTORY ${CMAKE_RUNTIME_OUTPUT_DIRECTORY})

enable_testing()

include(Catch)
catch_discover_tests(test-std-matrix)