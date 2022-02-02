# CMake toolchain analysis

[CMake](https://cmake.org) is an open-source, cross-platform family of tools
designed to build, test and package software. CMake is used to control the
software compilation process using simple platform and compiler independent
configuration files, and generate native makefiles and workspaces that can be
used in the compiler environment of your choice.

## Supported platforms

TODO: test cmake against currently Node.js supported platforms and toolchains
(see [BUILDING.MD](https://github.com/nodejs/node/edit/master/BUILDING.md)).

### Unsupported platforms

TODO: see above

## Pros

* Widely used by C++ projects (probably the most used toolchain besides of
  `make` and `autotools`).
* Easier to upgrade all our dependencies (except V8) and easier to add new
  dependencies that use or are compatible with CMake (which is likely based on
  previous point)
* It's been around for over two decades
* Due to its popularity, it's the most likely toolchain to support all of our
  platforms within our minimum version constraints

## Cons

* CMake is not on V8 tree, therefore, V8 upgrades would be just as hard as today
  with gyp


## Known ports

* No open source known ports [1^]

[1^]: It's not a full Node.js port, but
      [bnoordhuis/v8-cmake](https://github.com/bnoordhuis/v8-cmake) adds cmake
      support to V8

## Need more info

* Would cmake build affect Electron ability to build Node.js with GN in any way?

## Observations

* There seems to be positive reception at the idea of cmake for native modules,
  having the same build system for building Node.js and its native modules
* It is already possible to build node-addon-api based native modules with cmake.
* There is the possibility of using cmake to build everything except V8, using
  GN to build V8 and then linking it statically to Node.js
