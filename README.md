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
// file: test_fluidsynth.c
#include <fluidsynth.h>
int main(void)
{
    fluid_settings_t* settings = new_fluid_settings();
    delete_fluid_settings(settings);
    return 0;
}
```
## MSYS2, MinGW or Clang (x86_64-pc-windows-gnu)
1. Uncompress the package and copy the folders (bin, include, lib) into your MSYS2/MinGW/Clang installation folder (e.g. C:\\msys64\\mingw64)
2. Make sure that your `gcc`/`g++` are within the `PATH` environment variable.
2. Open MSYS2, cmd or PowerShell and use the `cd` command to change the working directory.
3. Type `gcc test_fluidsynth.c -lfluidsynth` to compile the simple program above.
4. 
