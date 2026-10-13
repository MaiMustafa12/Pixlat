
cmake_minimum_required(VERSION 3.20)

project(PIXLat LANGUAGES CXX RC)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_executable(PIXLat WIN32
    GUI/GUI.cpp
    PIXLat.rc
)

target_link_libraries(PIXLat PRIVATE
    gdiplus
    comctl32
    comdlg32
    gdi32
    user32
)
