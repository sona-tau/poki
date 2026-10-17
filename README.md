# Poki

<div align="center">
  <img src="https://raw.githubusercontent.com/lipu-linku/ijo/main/sitelenpona/static/poki-1.svg" width="50%" alt="pictogram of a container">
</div>


Poki is a program that lets you create C workspaces created with three core tenets:

1. reproducibility
2. portability
3. feature-complete

Poki will create a workspace meant for creating C libraries or executables. This workspace includes the following files:
- `flake.nix`
- `README.md`
- `include/AUTHOR/NAME.h`
- `src/NAME.c`
- `test/test.h`

``` text
.
├── CHANGELOG.md
├── flake.nix
├── include/AUTHOR/NAME.h
├── lib
│   ├── dynamic
│   └── static
├── LICENSE
├── nob.c
├── nob.h
├── README.md
├── src/NAME.c
└── tests/test.h

6 directories, 9 files
```


## Reproducibility

The `flake.nix` file declares all the necessary packages to work with and build a minimal C library. When using Nix, this produces a `flake.lock` artifact which specifies exactly what was needed to build the package.

The `flake.nix` file lets you include other Poki packages as inputs, tagged using Git Tags for versions or even specific commit hashes. Nix does the package management and the build system works with this.

The `flake.nix` file also produces a `NAME.pc` file that you can use with `pkg-config` and optionally installs files into `$DESTDIR$PREFIX`.

Usage of Nix is optional, and the structure of project files in the default configuration let you use any build system out of the box.

## Portability

This project relies on `nob.h` built by Tsoding: https://github.com/tsoding/nob.h/

This means that your C files can be built anywhere that has a C compiler. No complex build system needed.

## Feature-complete

This project attempts to be feature complete by providing:

- dynamic & static library targets
- release, debug & size-optimized targets
- testing
- fuzz-testing
- valgrind, strace, cppcheck and fmt-check for static cod verification
- builds documentation using Doxygen
- produces compile commands for use with any LSP
- other: can produce ctags and wrap the entire project into a tarball
