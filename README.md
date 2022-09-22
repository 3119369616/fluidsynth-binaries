# About this repository
We provide FluidSynth prebuilt binaries for __64-bit Windows__. Every binary is single-DLL. No depended DLLs!

------
# Supported ABIs
Although the binaries are built by Clang on native Windows, they can also used by **MSVC** and **MinGW-w64**.

-------
# Package structure
The binaries are 7-Zipped. Here is their folder structure:
```
bin/
    libfluidsynth-3.dll
    fluidsynth.exe
include/
        fluidsynth.h
        fluidsynth/
                   audio.h
                   event.h
                   XXX.h
lib/
    libfluidsynth.dll.a
    cmake/fluidsynth/
                     FluidSynthConfig.cmake
                     FluidSynthConfigVersion.cmake
                     XXX.cmake
    pkgconfig/
              fluidsynth.pc
```

---------
# How to use the binaries
## Write a simple program
```c

```
## MSYS, MinGW or Clang (x86_64-pc-windows-gnu)
1. Uncompress the package and copy the folders (bin, include, lib) into your MSYS/MinGW/Clang installation folder (e.g. C:\\msys64\\mingw64)
2. 
