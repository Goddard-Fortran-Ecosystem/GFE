# ChangeLog

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.20.0] - 2025-09-30

### Changed

- Update gFTL to v1.16.0
  - Require CMake 3.24
  - Updates for Windows Support
- Update gFTL-shared to v1.11.0
  - Update gFTL to v1.16.0
  - Require CMake 3.24
- Update fArgParse to v1.10.0
  - Update gFTL-shared to v1.11.0
  - Require CMake 3.24
- Update pFUnit to v4.13.0
  - Update fArgParse to v1.10.0
  - Bug fixes for ifx 2025.2
  - Updated support for Windows
  - Require CMake 3.24
- Update yaFyaml to v1.6.0
  - Support for ifx 2025.2
  - Require CMake 3.24
  - Update gFTL requirement to v1.16.0
  - Update gFTL-shared requirement to v1.11.0
- Update pFlogger to v1.17.0
  - Workaround for ifx 2025.2
  - Require CMake 3.24
  - Update gFTL requirement to v1.16.0
  - Update gFTL-shared requirement to v1.11.0
  - Update yaFyaml requirement to v1.6.0
- Remove `macos-13` from CI, add `macos-15`
- Add `gfortran-15` to macOS CI
- Update CMake minimum version to 3.24

## [1.19.0] - 2025-02-11

### Changed

- Update gFTL to v1.15.2
  - Eliminate debug prints

## [1.18.0] - 2025-02-06

### Changed

- Update pFlogger to v1.16.1
  - Revert use of `c_bool`

## [1.17.0] - 2025-02-04

### Changed

- Update gFTL to v1.15.1
  - New variant of Set container (compiler workaround)
- Update gFTL-shared to v1.10.0
  - Added support for LLVMFlang
- Update fArgParse to v1.9.0
  - LLVMFlang support and misc workarounds
- Update pFUnit to v4.11.1
  - Misc updates (support for Flang) and gfortran workarounds
- Update yaFyaml to v1.5.1
  - Flang support
  - Workaround for `ifx`
- Update pFlogger to v1.16.0
  - Flang support
- Update CI to have `gfortran-10` and `gfortran-11` only on `ubuntu-22.04`
- Update CI NVIDIA to NVHPC 24.7
- Add Flang to CI
- Removed `macos-13` from CI, use `macos-14`

## [1.16.0] - 2024-07-10

### Changed

- Update gFTL to v1.14.0
  - Added support for non-poly allocatable containers
- Update gFTL-shared to v1.9.0
  - Misc minor updates
- Update fArgParse to v1.8.0
  - Minor updates
- Update yaFyaml to v1.4.0
  - Workaround for gfortran 13.3 and minor updates to CI
- Update pFUinit to v4.10.0
  - Migrated to use v2 interfaces from gFTL
- Update CI to match that of pFUnit
  - Remove `macos-11` from GitHub Actions, add `macos-12` and `gfortran-14` to Ubuntu 24.04
- Update CI to NVHPC 24.5

## [1.15.0] - 2024-03-26

### Changed

- Update pFlogger to v1.14.0
  - Added `-quiet` flag for NAG Fortran
  - Workaround additional polymorphic assignment bug in gfortran 13.2 (in build_locks)

## [1.14.0] - 2024-03-20

### Changed

- Update gFTL to v1.13.0
  - ifx port
- Update pFlogger to v1.13.2
  - Bug fix
- Removed `macos-11` from CI as it is deprecated. Add `macos-13`

## [1.13.0] - 2024-03-07

### Changed

- Update gFTL to v1.12.0
  - Fujitsu compiler support (and other minor bugfixes)
- Update gFTL-shared to v1.8.0
  - Fujitsu compiler support
- Update fArgParse to v1.7.0
  - Fujitsu compiler support
  - Update to Apache 2.0 license
- Update pFUnit to v4.9.0
  - Fujitsu compiler support
  - Some bug fixes
- Update yaFyaml to v1.3.0
  - Fujitsu compiler support
  - GCC 13 fixes
- Update pFlogger to v1.13.1
  - Fujitsu compiler support
  - GCC 13 fixes
- Update CI to use Intel LLVM

## [1.12.0] - 2023-11-29

- Updated submodules for all repos. (See README)

## [1.11.0] - 2023-07-21

### Changed

- Update gFTL-shared to v1.6.1
  - Fixed issue where the names of some iterators for containers were not being correctly named.  E.g., StringSetIterator was only named SetIterator.
- Update pFUnit to v4.7.3
  - Fixed cmake issue where target "pfunit-mpi-defines" is defined more than once
  - Missing variable declaration in parameterized test case boiler plate code.

## [1.10.0] - 2023-04-17

### Changed

- Update gFTL to v1.10.0
  - Added `IntelLLVM.cmake` file as a copy of `Intel.cmake` to support the LLVM Intel compiler frontends
    (Note - this has not been tested due to lack of system access.)
  - Added Fortran-friendly iterator factories (and tests)
- Update gFTL-shared to v1.6.0
  - Added `IntelLLVM.cmake` file as a copy of `Intel.cmake` to support the LLVM Intel compiler frontends
  - Updated gFTL submodule to v1.10.0
- Update fArgParse to v1.5.0
  - Added `IntelLLVM.cmake` file as a copy of `Intel.cmake` to support the LLVM Intel compiler frontends
  - Updated submodules for gFTL-shared (v1.6.0)
  - implemented workaround for GFortran which was not correctly handling
    deferred-length allocatable string arrays.  Used StringVector instead.
- Update pFUnit to v4.7.0
  - Update fArgParse submodule to v1.5.0
  - Added IntelLLVM.cmake to support ifx
  - Added interface for `@asertEquals` for arrays of strings.   Previously only string scalars could be compared.
  - Added check in pFUnit preprocessor that raises an exception if the module name and filename do not agree unless `@suite` is used to override default assumptions.
  - Added option to set labels to ctests
  - Added changelog enforcer GitHub Action
  - `--verbose option` is now passed through by ctest runner
  - Converted GitHub CI to use cmake abstract build commands
- Update yaFyaml to v1.1.0
  - Added `IntelLLVM.cmake` file as a copy of `Intel.cmake` to support the LLVM Intel compiler frontends
  - Updated required gFTL version to v1.10.0
  - Updated required gFTL-shared version to v1.6.0
- Update pFlogger to v1.10.0
  - Added `IntelLLVM.cmake` file as a copy of `Intel.cmake` to support the LLVM Intel compiler frontends
  - Updated required version of gFTL to v1.10.0
  - Updated required version of gFTL-shared to v1.6.0
  - Updated required version of yaFyaml to v1.1.0

### Added

- Add GitHub Actions CI

## [1.9.0] - 2023-02-07

### Fixed

- Update gFTL to v1.8.3
  - Fixes for GNU Make builds
  - Missing `KIND=` on `size()` procedure. Gave incorrect response for large containers. Only affects V1 containers.
- Update gFTL-shared to v1.5.1
  - Fixes for GNU Make builds
- Update fArgParse to v1.4.2
  - Fixes for GNU Make builds
- Update pFUnit to v4.6.3
  - Fix for compilers that do not support 128 bit reals
  - Fixed build_submodule for old git versions
  - Fixed for use with FetchContent
  - Fix CMake logic in `add_pfunit_ctest.cmake` for `MPIEXEC_EXECUTABLE`. Problem not exposed by common MPI flavors which use `mpirun`
  - Fix GitHub CI workflow by pinning to CMake 3.24.3
  - Fixes for GNU Make builds
  - Update fArgParse submodule to v1.4.2
  - Fix `pFUnitParser.py` in cases where there is no module name
- Update yaFyaml to v1.0.7
  - Workaround for NVIDIA compiler
  - Fixes for GNU Make builds
  - Workarounds for Intel 2021.7
  - Out of date examples have been updated
- Update pFlogger to v1.9.3
  - Fixes for GNU Make builds
  - Package was incorrectly assuming that all extant compilers support 128 bit reals. Now a check is performed to optionally include support for 128 bit reals.
  - Fix `Parser()` declaration for Intel 2021.7

## [1.8.0] - 2022-11-15

### Changed

- Change behavior if user does not pass in `CMAKE_INSTALL_PREFIX` to put install directory inside build (as we are know we can
  write there; default for CMake install is `/usr/local`)
  
### Added

- Added `CODEOWNERS` file

## [1.7.0] - 2022-11-15

### Changed

- Update pFUnit to v4.6.1 (bug fix)

## [1.6.0] - 2022-11-09

### Changed

- Update pFUnit to v4.6.0

## [1.5.0] - 2022-11-07

### Changed

- Updated fArgParse to v1.4.1
- Updated pFUnit to v4.5.0
- Updated details in README

## [1.4.0] - 2022-06-30

### Changed

- Updated rev of gFTL  to v1.8.1 (fix for documentation tool)
- Updated rev of yaFyaml to v1.0.4 (better error handling and bugfix for anchors)

## [1.3.1] - 2022-06-02

### Changed

- Botched the fArgParse commit in previous release.  (Minor, but SHA was not on GitHub so ...)

## [1.3.0] - 2022-06-01

### Fixed

- Various - consult submodules;  mostly compiler workarounds.

## [1.2.0] - 2022-05-08

### Changed

- updated submodules
  - gFTL v1.7.2
  - yaFyaml v1.0.0 (now formally released.  No longer in beta.)
  - pFlogger v1.9.0


### Fixed

- Includes yaFyaml update that has critical workarounds for compilers (mostly gFortran)

## [1.1.2] - 2022-04-24

### Fixed

- Updated gFTL to include a bugfix.

## [1.1.1] - 2022-04-21

### Fixed

- Updated pFunit to include a bugfix.

## [1.1.0] - 2022-04-20

## Changed

- Updated git submodule URLs to relative URLs
- Fixed typos in README

## Added

- Added GitHub Action to make a release tarball

## [1.0.3] - 2022-04-19

## Changed

- Minor bugfix update to pFUnit (v4.2.7)

## [1.0.2] - 2022-04-19

## Changed

- Update pFUnit to absorb critical bugfix (v4.2.6)

## [1.0.1] - 2022-04-11

### Changed

- Changed default branch to be `main` and fixed typos in README.

## [1.0.0] - 2022-04-08

Initial release

| Package     | Version |
| :------     | :------ |
| gFTL        | v1.7.0  |
| gFTL-shared | v1.4.1 |
| fArgParse   | v1.2.0 |
| yaFyaml     | v1.0-beta8 |
| pFlogger    | v1.8.0 |
| pFUnit      | v4.2.5 |

