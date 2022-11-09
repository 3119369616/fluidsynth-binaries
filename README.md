# About this repository
We provide FluidSynth prebuilt binaries for __64-bit Windows__. Every binary is single-DLL. No depended DLLs!

------
# Supported ABIs
Although the binaries are built by Clang on native Windows, they can also used by **MSVC** and **MinGW-w64**.

-------
# Package structure
The binaries are 7-Zipped. Here is their folder structure:
```
bin/                       == A folder including DLLs and EXEs. ==
    libfluidsynth-3.dll    == The FluidSynth shared library ==
    fluidsynth.exe         == The FluidSynth program ==
include/                      == FluidSynth's C/C++ header files. Just #include <fluidsynth.h>. ==
        fluidsynth.h          == The header file you have to include.
        fluidsynth/           == Other header files... == 
                   audio.h    
                   event.h
                   ...
lib/                                                  == Libraries for linker ++
    libfluidsynth.dll.a                               == The import library corresponding to "libfluidsynth-3.dll" ==
    cmake/fluidsynth/                                 == CMake configuration files that you can use in your project with CMake. 
                                                         (There isn't a "cmake" folder in FluidSynth 2.2.x) ==
                     FluidSynthConfig.cmake
                     FluidSynthConfigVersion.cmake
                     ...
    pkgconfig/                                        == The pkg-config configuration metadata file ==
              fluidsynth.pc
```

---------
# How to use the binaries
Uncompress the package that you've downloaded and then write the simple program below:
## A simple program
```c
// file: test_fluidsynth.c
#include <fluidsynth.h>
#include <stdio.h>
int main(void)
{
    fluid_settings_t* settings = new_fluid_settings();
    if(!settings)
    {
        puts("ERROR: cannot create a 'settings' instance.");
        return -1;
    }
    delete_fluid_settings(settings);
    puts("A simple test of FluidSynth is OK.");
    return 0;
}
```
## Compile it in MSYS2, MinGW or Clang (x86_64-pc-windows-gnu)
1. Copy the folders (**bin, include, lib**) into your MSYS2/MinGW/Clang installation folder (e.g. C:\\msys64\\mingw64)
2. Make sure that your `gcc` and `g++` is in the PATH environment variable.
2. Open MSYS2, cmd or PowerShell and use the `cd` command to change the working directory.
3. Type `gcc test_fluidsynth.c -lfluidsynth` to compile the simple program above.
4. If there are NO compilation errors, run the simple program `a.exe` and you'll see the output:
     ```
     A simple test of FluidSynth is OK.
     ```
## Compile it with Visual C++
This part is still in busy experiments. We will improve the tutorial for it in the future.
### Compiling in the command prompt of Visual Studio
**Note**: You must use `x64 Native Tools Command Prompt for VS 20XX`. DO NOT USE `Developer Command Prompt for VS 20XX`!
1. Input `cl test_fluidsynth.c /GR /EHsc /MD /O2 /Ob2 /DNDEBUG /link:C` 
