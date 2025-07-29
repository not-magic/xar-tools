# xar-tools

A fixed build system to be able to compile xar and pbzx as static executables. 


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

