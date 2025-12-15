# Local Map Upgrade

Fork to attempt to manipulate Quest Markers in Local Map

## Project Setup

### 1. Dependencies Setup

1. Download and install [CMake](https://cmake.org/download/)
2. Download and install [vcpkg](https://github.com/microsoft/vcpkg)
3. Set the `VCPKG_ROOT` windows environment variable to the directory donwloaded above in 2. (or where it was moved to)
4. Run the initialisation bootstrap-vcpkg.bat file
5. Download and install [git](https://git-scm.com/downloads/win) and/or [GitHub Desktop](https://desktop.github.com/download/)
6. Download [Visual Studio 2022](https://visualstudio.microsoft.com/)
7. In Visual Studio Installer, install "Desktop Development with C++"

### 2. Modify CMakeList.txt

1. Change `SKYRIM_SE_DIR` to your root Skyrim folder
2. Change `set(COPY_VR NO)` to `set(COPY_VR YES)` in the conditional code block `if ("$ENV{RUNTIME_DISABLE_FLAGS}" STREQUAL "")` or simply create a empty windows environment variable `RUNTIME_DISABLE_FLAGS`

### 3. Let it Rip

1. Visual Studio automatically builds and sends the `.dll` file to `SKYRIM_SE_DIR`

### 4. Skyrim Setup (Optional)

This will allow to attach to process for debug

1. Download Skyrim from Steam and change its folder name
2. Run [Steamless](https://github.com/atom0s/Steamless) to remove Steam DRM
3. Build SKSE64 instead of installing from the mod page (to properly attach Skyrim to Debug in VSCode)
  ```
  git clone https://github.com/ianpatt/common
  git clone https://github.com/ianpatt/skse64
  cmake -B common/build -S common -DCMAKE_INSTALL_PREFIX=extern
  cmake --build common/build --config Debug --target install
  cmake -B skse64/build -S skse64 -DCMAKE_INSTALL_PREFIX=extern
  cmake --build skse64/build --config Debug
  ```
4. Copy the following files to Skryim Root directory
  - `skse64/build/skse64/Debug/skse64_1_6_***.dll`
  - `skse64/build/skse64/Debug/skse64_1_6_***.pdb`
  - `skse64/build/skse64_loader/Debug/skse64_loader.exe`
  - `skse64/build/skse64_loader/Debug/skse64_loader.pdb`
  - `skse64/build/skse64_steam_loader/Debug/skse64_steam_loader.dll`
  - `skse64/build/skse64_steam_loader/Debug/skse64_steam_loader.pdb`
5. Download [Address Library](https://www.nexusmods.com/skyrimspecialedition/mods/32444) mod and install

### 5. Attach debuger in Visual Studio (Optional)

1. Make sure you follow step `4.`
1. TODO...
