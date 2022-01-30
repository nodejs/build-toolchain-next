# Bazel toolchain analysis

[Bazel](https://bazel.build/) is an open-source build and test tool similar to
Make, Maven, and Gradle. It uses a human-readable, high-level build language.
Bazel supports projects in multiple languages and builds outputs for multiple
platforms. Bazel supports large codebases across multiple repositories, and
large numbers of users.

## Supported platforms

TODO: test Bazel against currently Node.js supported platforms and toolchains
(see [BUILDING.MD](https://github.com/nodejs/node/edit/master/BUILDING.md)).

### Unsupported platforms

TODO: see above

## Pros

* Easier to upgrade V8 as we don't need to rewrite build configs for V8
* Compared to GN, Bazel is more widely adopted outside Chromium

## Cons

* Other dependencies will need Node.js-maintained GN build files
* Currently support a limited set of platforms [^1]
* V8 team can't guarantee Bazel will still be maintained if V8 stops being used
  at Google outside Chroumium

[^1]: There's a registry of community-maintained build files for popular
projects. It still doesn't cover several dependenceis that Node.js needs but
might be a better place to have those files instead of keeping them in Node.js
itself https://github.com/bazelbuild/bazel-central-registry/blob/main/modules/.

## Known ports

* No known open-source ports


## Need more info

* Could V8 use Bazel instead of GN in their CI?

## Observations

*
