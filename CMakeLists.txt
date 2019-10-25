cmake_minimum_required(VERSION 3.13)
project(world-builder-dependencies VERSION 1.0.0 LANGUAGES CXX)
include(GNUInstallDirs)

function(target_sources_public target)
  # Must be using CMake 3.12 or earlier, so simulate the new behavior
  unset(_srcList)
  foreach(src ${ARGN})
    list(APPEND _srcList "$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/${src}>")
    list(APPEND _srcList "$<INSTALL_INTERFACE:include/${src}>")
  endforeach()
  target_sources(${target} PUBLIC ${_srcList})
endfunction()

function(target_sources_interface target)
  # Must be using CMake 3.12 or earlier, so simulate the new behavior
  unset(_srcList)
  foreach(src ${ARGN})
    list(APPEND _srcList "$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/${src}>")
    list(APPEND _srcList "$<INSTALL_INTERFACE:include/${src}>")
  endforeach()
  target_sources(${target} INTERFACE ${_srcList})
endfunction()

add_subdirectory(GeometricTools)
