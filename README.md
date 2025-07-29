# xar-tools

An updated build system (using cmake) to be able to compile pbzx and xar as static executables, because I was unable to get it functioning with the original build scripts.

# Compiling (Linux)

First submodules must be installed (the xar amd pbzx sources are taken as-is from their githubs)
```
git submodule update
```
Next create the build folder and compile it

```
mkdir build
cd build
cmake ..
make
```

## Dependencies

* LibXml2
* ZLIB
* LibLZMA
* OpenSSL

