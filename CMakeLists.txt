cmake_minimum_required(VERSION 3.0)
project(hazel-app)

add_library(hazel SHARED 
    Hazel/src/Hazel/Application.cpp
)

target_include_directories(hazel PUBLIC 
    ${PROJECT_SOURCE_DIR}/Hazel/
    ${PROJECT_SOURCE_DIR}/Hazel/src/
)

add_executable(hazel-app  
    Sandbox/src/SandboxApp.cpp
)

target_include_directories(hazel-app PUBLIC
    ${PROJECT_SOURCE_DIR}/Hazel/
    ${PROJECT_SOURCE_DIR}/Hazel/src/
)

target_compile_definitions(hazel PRIVATE 
    HZ_PLATFORM_WINDOWS 
    HZ_BUILD_DLL
)

target_compile_definitions(hazel-app PRIVATE 
    HZ_PLATFORM_WINDOWS 
)

target_link_libraries(hazel-app PRIVATE hazel)