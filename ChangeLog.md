# ChangeLog

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.9.0] - 2023-01-27

### Fixed

- Update gFTL to v1.8.3
  - Fixes for GNU Make builds
  - Missing `KIND=` on `size()` procedure. Gave incorrect response for large containers. Only affects V1 containers.
- Update gFTL-shared to v1.5.1
  - Fixes for GNU Make builds
- Update fArgParse to v1.4.2
  - Fixes for GNU Make builds
- Update pFUnit to v4.6.2
  - Fixed build_submodule for old git versions
  - Fixed for use with FetchContent
  - Fix CMake logic in `add_pfunit_ctest.cmake` for `MPIEXEC_EXECUTABLE`. Problem not exposed by common MPI flavors which use `mpirun`
  - Fix GitHub CI workflow by pinning to CMake 3.24.3
  - Fixes for GNU Make builds
  - Update fArgParse submodule to v1.4.2
  - Fix `pFUnitParser.py` in cases where there is no module name
- Update yaFyaml to v1.0.6
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

