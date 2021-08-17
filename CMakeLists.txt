cmake_minimum_required(VERSION 3.19)
project(palka)
set(CMAKE_CXX_STANDARD 17)

if(${CMAKE_BUILD_TYPE} MATCHES "Debug")
    set(CMAKE_CXX_FLAGS "-O0 -g")
else()
    set(CMAKE_CXX_FLAGS "-O3 -mwindows -DNDEBUG -s")
endif()

set(SDLTTFDIR /usr/include/SDL2/)


find_package(SDL2 REQUIRED)
find_package(Freetype REQUIRED)
find_package(RTTR CONFIG REQUIRED Core)
find_package(OpenGL REQUIRED)
find_package(SDL_ttf REQUIRED)
find_package(SDL_image REQUIRED)

add_executable(palka Source.cpp)

target_link_libraries(palka mingw32 ${SDLTTF_LIBRARY} Freetype::Freetype SDL2::SDL2main SDL2::SDL2 ${OPENGL_LIBRARIES} ${GLUT_LIBRARY} ${SDL_IMAGE_LIBRARIES} RTTR::Core imm32)
target_compile_definitions(palka PUBLIC IMGUI_IMPL_OPENGL_LOADER_GLAD GL_GLEXT_PROTOTYPES=1)
