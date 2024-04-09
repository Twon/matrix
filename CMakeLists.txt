cmake_minimum_required(VERSION 3.21)

if(NOT DEFINED PROJECT_NAME)
    set(STD_MATRIX_IS_PRIMARY_PROJECT ON)
endif()

project(wg21-linear-algebra-matrix VERSION 0.8.0)

include(CTest)
include(FetchContent)
include(GNUInstallDirs)
include(CMakeDependentOption)
include(CMakePackageConfigHelpers)

cmake_dependent_option(MATRIX_ENABLE_TESTS "Enable std::math:linear_algebra tests" ON "BUILD_TESTING" OFF)

add_library(std-matrix INTERFACE)
target_include_directories(std-matrix
    INTERFACE
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
        $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>
)

set_target_properties(std-matrix
    PROPERTIES
        CXX_STANDARD 23
        CXX_STANDARD_REQUIRED YES
        CXX_EXTENSIONS NO
)

target_compile_features(std-matrix
    INTERFACE
        cxx_std_23
)

set_target_properties(std-matrix
    PROPERTIES
        RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin
)

if (${MATRIX_ENABLE_TESTS})
    add_subdirectory(tests)
endif()