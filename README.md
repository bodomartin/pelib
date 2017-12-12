## PeLib

PE file manipulation library. The [original](http://www.pelib.com/index.php) project by Sebastian Porst was further modified by Avast Software to:
* Modify directory structure, i.e. split sources and headers.
* Fix bugs.
* Handle corrupted and exotic PE files.
* Parse additional structures:
  * COFF symbol table.
  * Delay import directory.
  * Rich header.
  * Security directory.

## Use

A single target named `pelib` is exposed. It can be used as follows:
```cmake
target_link_libraries(project-that-needs-pelib pelib)
```

## Requirements

* A compiler supporting C++14
 * On Windows, only Microsoft Visual C++ is supported (version >= Visual Studio 2015).
* CMake (version >= 3.6)

## Build and Installation

* Clone the repository or download the sources into a directory named `pelib`.
  * `git clone https://github.com/avast-tl/pelib.git`
* Linux:
  * `cd pelib`
  * `mkdir build && cd build`
  * `cmake .. -DCMAKE_INSTALL_PREFIX=<path>`
  * `make && make install`
* Windows:
  * Open MSBuild command prompt, or any terminal that is configured to run the `msbuild` command.
  * `cd pelib`
  * `mkdir build && cd build`
  * `cmake .. -DCMAKE_INSTALL_PREFIX=<path> -G<generator>`
  * `msbuild /m /p:Configuration=Release pelib.sln`
  * `msbuild /m /p:Configuration=Release INSTALL.vcxproj`
  * Alternatively, you can open `pelib.sln` generated by `cmake` in Visual Studio IDE.

You must pass the following parameters to `cmake`:
* `-DCMAKE_INSTALL_PREFIX=<path>` to set the installation path to `<path>`.
* (Windows only) `-G<generator>` is `-G"Visual Studio 14 2015"` for 32-bit build using Visual Studio 2015, or `-G"Visual Studio 14 2015 Win64"` for 64-bit build using Visual Studio 2015. Later versions of Visual Studio may be used.

You can pass additional parameters to `cmake`:
* `-DCMAKE_BUILD_TYPE=Debug` to build with debugging information, which is useful during development. By default, the project is built in the `Release` mode. This has no effect on Windows, but the same thing can be achieved by running `msbuild` with the `/p:Configuration=Debug` parameter.

## License

The original PeLib modules:
* Copyright (c) 2004 - 2005 Sebastian Porst (webmaster@the-interweb.com), licensed under the zlib/libpng License. See the `ZLIB_LICENSE` file for more details.

Modules added by Avast Software:
* Copyright (c) 2017 Avast Software, licensed under the MIT license. See the `MIT_LICENSE` file for more details.

## Contributing

See [RetDec contribution guidelines](https://github.com/avast-tl/retdec/wiki/Contribution-Guidelines).
