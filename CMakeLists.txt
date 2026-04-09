cmake_minimum_required(VERSION 3.24)
project (GFE
  VERSION 1.25.0
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

# Pass down option to enable building of tests in subdirectories
set(ENABLE_TESTS ON CACHE BOOL "Enable building of tests")

# Define canonical test targets here before any subproject can claim them.
# Each subproject uses "if (NOT TARGET tests/build-tests)" guards, so they
# will skip their own definitions and simply call add_dependencies() against
# these targets.  This ensures:
#   - "tests" runs ctest from the correct top-level build directory
#   - "tests" always depends on "build-tests" (used by pFUnit/yaFyaml)
#   - "build-tests" compiles all test binaries before ctest is invoked
if (NOT TARGET build-tests)
  add_custom_target(build-tests)
endif()
if (NOT TARGET tests)
  add_custom_target(tests
    COMMAND ${CMAKE_CTEST_COMMAND} --output-on-failure
    WORKING_DIRECTORY ${CMAKE_BINARY_DIR}
    DEPENDS build-tests)
endif()

add_subdirectory(gFTL)
add_subdirectory(gFTL-shared)
add_subdirectory(fArgParse)
add_subdirectory(pFUnit)
add_subdirectory(yaFyaml)
add_subdirectory(pFlogger)

# https://www.scivision.dev/cmake-auto-gitignore-build-dir/
# --- auto-ignore build directory
if(NOT EXISTS ${PROJECT_BINARY_DIR}/.gitignore)
  file(WRITE ${PROJECT_BINARY_DIR}/.gitignore "*")
endif()

# Piggyback that file into install
install(
  FILES ${PROJECT_BINARY_DIR}/.gitignore
  DESTINATION ${CMAKE_INSTALL_PREFIX}
)
