project(visualization.pictureit)

cmake_minimum_required(VERSION 2.6)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${PROJECT_SOURCE_DIR})

find_package(kodi REQUIRED)
find_package(OpenGL)

if(OPENGL_FOUND)
  find_package(SOIL REQUIRED)
  set(INCLUDES ${OpenGL_INCLUDE_DIR}
               ${SOIL_INCLUDE_DIRS})
  add_definitions(-DHAS_OPENGL -DHAS_GL)
  set(DEPLIBS ${OPENGL_LIBRARIES} ${SOIL_LIBRARIES})
else()
  message(FATAL_ERROR "Unimplemented rendering API! Currently this add-on is only available for OpenGL")
endif()

include_directories(${INCLUDES}
                    ${KODI_INCLUDE_DIR}
                    ${PROJECT_SOURCE_DIR}/lib/kissfft
                    ${CMAKE_INCLUDE_PATH})

add_subdirectory(lib/kissfft)

set(PICTUREIT_SOURCES src/mrfft.cpp
                      src/pictureit.cpp)

list(APPEND DEPLIBS kissfft)

if(APPLE)
  set(DEPLIBS ${DEPLIBS} "-framework CoreVideo")
endif()

add_options(CXX ALL_BUILDS -std=c++11)

build_addon(visualization.pictureit PICTUREIT DEPLIBS)

include(CPack)
