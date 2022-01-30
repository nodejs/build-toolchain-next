# GN toolchain analysis

[GN](https://gn.googlesource.com/gn/) is a meta-build system developed by Google
that generates build files for Ninja. It is currently the official build system
for V8 and Chromium, it is used to build Node.js on Fuchsia, and is also used by
open source projects like Electron.

## Supported platforms

TODO: test GN against currently Node.js supported platforms and toolchains (see
[BUILDING.MD](https://github.com/nodejs/node/edit/master/BUILDING.md)).

### Unsupported platforms

TODO: see above

## Pros

* Easier to upgrade V8 as we don't need to rewrite build configs for V8
* V8, Fuchsia and Electron already have GN files for Node.js. Unifying those in
  the Node.js repository might be easier than writing build files for a
  different toolchain
* Projects integrating Node.js and Chromium don't need to maintain their own GN
  build files for Node.js
* Extensibility should allow implementation of custom features or platforms

## Cons

* Other dependencies will need Node.js-maintained GN build files
* Chromium team does not recommend using GN outside Chromium [^1]
* V8 team can't guarantee GN will still be maintained
* Add extra dependencies (`gn`, `ninja`, `build`, `buildtools`, etc.)
* `depot_tools` is cumbersome for non-Google engineers, but not using it means
  we would be using GN in a non-supported way

[^1]: Electron team had good experiences asking GN team for help in the past

## Known ports

* [node-ci](https://chromium.googlesource.com/v8/node-ci/): Node.js built with
  GN to run on Google CI infrastructure
* [electron patch](https://github.com/electron/electron/blob/main/patches/node/build_add_gn_build_files.patch)
  to add GN build files to Node.js
* Fuchsia Node.js build uses GN


## Need more info

* Can GN be used in a hybrid approach where other dependencies are built with
  their own toolchains (like CMake)?
* How well does it work with gcc and other non-clang compilers?
* How to generate the files needed for building native modules, assuming GN will
  not be used for native modules?
* Using GN means we'll also be using ninja instead of make?

## Observations

* If agreed among projects, burden of GN build files maintenance can be shared
  between Node.js, V8, Electron, and any other interested projects.
* There is also the possibility of using GN to build V8 alone and use something
  else for the rest of the project
* Assuming we land on another toolchain, would it stil be possible to have GN
  build files on the project to better integrate with V8 tests as well as
  Electron and Fuchsia build workflows?
