cmake_minimum_required(VERSION 3.16)

project(mlf VERSION 0.1 LANGUAGES CXX)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)

find_package(Qt6 REQUIRED
    COMPONENTS
        Widgets
)

set(PROJECT_HEADERS
    src/mainwindow.h
)

set(PROJECT_SOURCES
    src/main.cpp
    src/mainwindow.cpp
)

set(PROJECT_FORMS
    src/mainwindow.ui
)

qt_add_executable(mlf
    ${PROJECT_SOURCES}
    ${PROJECT_HEADERS}
    ${PROJECT_FORMS}
)

set_target_properties(mlf PROPERTIES
    ARCHIVE_OUTPUT_DIRECTORY
        "${CMAKE_BINARY_DIR}/lib"
    LIBRARY_OUTPUT_DIRECTORY
        "${CMAKE_BINARY_DIR}/lib"
    RUNTIME_OUTPUT_DIRECTORY
        "${CMAKE_BINARY_DIR}/bin"
)

target_compile_features(mlf PRIVATE
    cxx_std_17
)

target_link_libraries(mlf PRIVATE
    Qt6::Widgets
)
