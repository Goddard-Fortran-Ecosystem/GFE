cmake_minimum_required(VERSION 3.12)
project (GFE
  VERSION 1.13.0
  LANGUAGES Fortran
)
cmake_policy(SET CMP0074 NEW)

# Most users of this software do not (should not?) have permissions to
# install in the cmake default of /usr/local (or equiv on other os's).
# Below, the default is changed to a directory within the build tree
# unless the user explicitly sets CMAKE_INSTALL_PREFIX in the cache.
if (CMAKE_INSTALL_PREFIX_INITIALIZED_TO_DEFAULT)
    set (CMAKE_INSTALL_PREFIX "${CMAKE_BINARY_DIR}/installed" CACHE PATH "default install path" FORCE )
    message(STATUS "*** Setting default install prefix to ${CMAKE_INSTALL_PREFIX}.")
    message(STATUS "*** Override with -DCMAKE_INSTALL_PREFIX=<path>.")
endif()

enable_testing()

add_subdirectory(gFTL)
add_subdirectory(gFTL-shared)
add_subdirectory(fArgParse)
add_subdirectory(pFUnit)
add_subdirectory(yaFyaml)
add_subdirectory(pFlogger)
