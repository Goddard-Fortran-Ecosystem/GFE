cmake_minimum_required(VERSION 3.24)
project (GFE
  VERSION 1.21.0
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

#add_subdirectory(gFTL)
#add_subdirectory(gFTL-shared)
#add_subdirectory(fArgParse)
#add_subdirectory(pFUnit)
#add_subdirectory(yaFyaml)
#add_subdirectory(pFlogger)

include(ExternalProject)

ExternalProject_Add(gFTL
  SOURCE_DIR ${CMAKE_CURRENT_LIST_DIR}/gFTL

  CMAKE_ARGS
     -DCMAKE_INSTALL_PREFIX:PATH=<INSTALL_DIR>
     -DCMAKE_PREFIX_PATH:PATH=${CMAKE_INSTALL_PREFIX}

  BUILD_COMMAND $(MAKE)

  INSTALL_COMMAND $(MAKE) install
  INSTALL_DIR ${CMAKE_INSTALL_PREFIX}

  #LOG_DIR               ${CMAKE_INSTALL_PREFIX}/logs/gFTL
  #LOG_CONFIGURE         TRUE
  #LOG_BUILD             TRUE
  #LOG_INSTALL           TRUE
  #LOG_MERGED_STDOUTERR  TRUE
  #LOG_OUTPUT_ON_FAILURE TRUE
  )

ExternalProject_Add(gFTL-shared
  SOURCE_DIR ${CMAKE_CURRENT_LIST_DIR}/gFTL-shared

  CMAKE_ARGS
     -DCMAKE_INSTALL_PREFIX:PATH=<INSTALL_DIR>
     -DCMAKE_PREFIX_PATH:PATH=${CMAKE_INSTALL_PREFIX}

  BUILD_COMMAND $(MAKE)

  INSTALL_COMMAND $(MAKE) install
  INSTALL_DIR ${CMAKE_INSTALL_PREFIX}

  #LOG_DIR               ${CMAKE_INSTALL_PREFIX}/logs/gFTL-shared
  #LOG_CONFIGURE         TRUE
  #LOG_BUILD             TRUE
  #LOG_INSTALL           TRUE
  #LOG_MERGED_STDOUTERR  TRUE
  #LOG_OUTPUT_ON_FAILURE TRUE

  DEPENDS gFTL
  )

ExternalProject_Add(fArgParse
  SOURCE_DIR ${CMAKE_CURRENT_LIST_DIR}/fArgParse

  CMAKE_ARGS
     -DCMAKE_INSTALL_PREFIX:PATH=<INSTALL_DIR>
     -DCMAKE_PREFIX_PATH:PATH=${CMAKE_INSTALL_PREFIX}

  BUILD_COMMAND $(MAKE)

  INSTALL_COMMAND $(MAKE) install
  INSTALL_DIR ${CMAKE_INSTALL_PREFIX}

  #LOG_DIR               ${CMAKE_INSTALL_PREFIX}/logs/fArgParse
  #LOG_CONFIGURE         TRUE
  #LOG_BUILD             TRUE
  #LOG_INSTALL           TRUE
  #LOG_MERGED_STDOUTERR  TRUE
  #LOG_OUTPUT_ON_FAILURE TRUE

  DEPENDS gFTL
  DEPENDS gFTL-shared
  )

ExternalProject_Add(pFUnit
  SOURCE_DIR ${CMAKE_CURRENT_LIST_DIR}/pFUnit

  CMAKE_ARGS
     -DCMAKE_INSTALL_PREFIX:PATH=<INSTALL_DIR>
     -DCMAKE_PREFIX_PATH:PATH=${CMAKE_INSTALL_PREFIX}
     -DSKIP_OPENMP=${SKIP_OPENMP}

  BUILD_COMMAND $(MAKE)

  INSTALL_COMMAND $(MAKE) install
  INSTALL_DIR ${CMAKE_INSTALL_PREFIX}

  #LOG_DIR               ${CMAKE_INSTALL_PREFIX}/logs/pFUnit
  #LOG_CONFIGURE         TRUE
  #LOG_BUILD             TRUE
  #LOG_INSTALL           TRUE
  #LOG_MERGED_STDOUTERR  TRUE
  #LOG_OUTPUT_ON_FAILURE TRUE

  DEPENDS gFTL
  DEPENDS gFTL-shared
  DEPENDS fArgParse
  )

ExternalProject_Add(yaFyaml
  SOURCE_DIR ${CMAKE_CURRENT_LIST_DIR}/yaFyaml

  CMAKE_ARGS
     -DCMAKE_INSTALL_PREFIX:PATH=<INSTALL_DIR>
     -DCMAKE_PREFIX_PATH:PATH=${CMAKE_INSTALL_PREFIX}

  BUILD_COMMAND $(MAKE)

  INSTALL_COMMAND $(MAKE) install
  INSTALL_DIR ${CMAKE_INSTALL_PREFIX}

  #LOG_DIR               ${CMAKE_INSTALL_PREFIX}/logs/yaFyaml
  #LOG_CONFIGURE         TRUE
  #LOG_BUILD             TRUE
  #LOG_INSTALL           TRUE
  #LOG_MERGED_STDOUTERR  TRUE
  #LOG_OUTPUT_ON_FAILURE TRUE

  DEPENDS gFTL
  DEPENDS gFTL-shared
  )

ExternalProject_Add(pFlogger
  SOURCE_DIR ${CMAKE_CURRENT_LIST_DIR}/pFlogger

  CMAKE_ARGS
     -DCMAKE_INSTALL_PREFIX:PATH=<INSTALL_DIR>
     -DCMAKE_PREFIX_PATH:PATH=${CMAKE_INSTALL_PREFIX}

  BUILD_COMMAND $(MAKE)

  INSTALL_COMMAND $(MAKE) install
  INSTALL_DIR ${CMAKE_INSTALL_PREFIX}

  #LOG_DIR               ${CMAKE_INSTALL_PREFIX}/logs/pFlogger
  #LOG_CONFIGURE         TRUE
  #LOG_BUILD             TRUE
  #LOG_INSTALL           TRUE
  #LOG_MERGED_STDOUTERR  TRUE
  #LOG_OUTPUT_ON_FAILURE TRUE

  DEPENDS gFTL
  DEPENDS gFTL-shared
  DEPENDS yaFyaml
  )

ExternalProject_Add_Step(gFTL tests
  COMMAND           $(MAKE) tests
  WORKING_DIRECTORY <BINARY_DIR>
  COMMENT           "Building gFTL tests"
  EXCLUDE_FROM_MAIN TRUE
)
ExternalProject_Add_StepTargets(gFTL tests)

ExternalProject_Add_Step(pFUnit tests
  COMMAND           $(MAKE) tests
  WORKING_DIRECTORY <BINARY_DIR>
  COMMENT           "Building pFUnit tests"
  EXCLUDE_FROM_MAIN TRUE
)
ExternalProject_Add_StepTargets(pFUnit tests)

ExternalProject_Add_Step(pFlogger tests
  COMMAND           $(MAKE) tests
  WORKING_DIRECTORY <BINARY_DIR>
  COMMENT           "Building pFlogger tests"
  EXCLUDE_FROM_MAIN TRUE
)
ExternalProject_Add_StepTargets(pFlogger tests)

ExternalProject_Add_Step(fArgParse tests
  COMMAND           $(MAKE) tests
  WORKING_DIRECTORY <BINARY_DIR>
  COMMENT           "Building fArgParse tests"
  EXCLUDE_FROM_MAIN TRUE
)
ExternalProject_Add_StepTargets(fArgParse tests)

ExternalProject_Add_Step(yaFyaml tests
  COMMAND           $(MAKE) tests
  WORKING_DIRECTORY <BINARY_DIR>
  COMMENT           "Building yaFyaml tests"
  EXCLUDE_FROM_MAIN TRUE
)
ExternalProject_Add_StepTargets(yaFyaml tests)
