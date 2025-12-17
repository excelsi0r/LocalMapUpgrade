# Local Map Upgrade

Fork to attempt to manipulate Quest Markers in Local Map

## Project Setup

### 1. Dependencies Setup

1. Download and install [git](https://git-scm.com/downloads/win)
1. (Optional) Install [GitHub Desktop](https://desktop.github.com/download/) if you want to use it
1. Make sure to git clone [vcpkg](https://github.com/microsoft/vcpkg). **NEVER** download the `.zip` file or an official installer. It needs to be downloaded as a `.git` repository
	```
	git clone https://github.com/microsoft/vcpkg.git C:\vcpkg
	``` 
1. Set the `VCPKG_ROOT` windows environment variable to the directory donwloaded above in 3. In this case `C:\vcpkg`. Both user and system variables.
1. Double-click the initialisation script `C:\vcpkg\bootstrap-vcpkg.bat`
1. Download and install [Visual Studio 2026 Community](https://visualstudio.microsoft.com/)
1. In Visual Studio Installer, install "Desktop Development with C++" and only the following required optional features:
	- MSVC Build Tools for x64/x86 (Latest)
	- C++ CMaker tools for Windows
	- Windows 11 SDK

### 2. Set Skyrim Installation folder

1. In case of a different installation folder, modify CMakeList.txt file by setting the variable `SKYRIM_SE_DIR` to your root Skyrim folder 

### 3. Let it Rip

1. Chose "Debug (SE only)" given we are not building for VR now
1. Build the project by going to **Build** > **Build All**. Visual Studio automatically builds and sends the `.dll` file to `SKYRIM_SE_DIR`

### 4. (Optional) Skyrim Setup 

This will allow to attach to process for debug

1. Download Skyrim from Steam and change its folder name
1. Run [Steamless](https://github.com/atom0s/Steamless) to remove Steam DRM
1. Build SKSE64 instead of installing from the mod page (to properly attach Skyrim to Debug in VSCode)
  ```
  git clone https://github.com/ianpatt/common
  git clone https://github.com/ianpatt/skse64
  cmake -B common/build -S common -DCMAKE_INSTALL_PREFIX=extern
  cmake --build common/build --config Debug --target install
  cmake -B skse64/build -S skse64 -DCMAKE_INSTALL_PREFIX=extern
  cmake --build skse64/build --config Debug
  ```
1. Copy the following files to Skryim Root directory
  - `skse64/build/skse64/Debug/skse64_1_6_***.dll`
  - `skse64/build/skse64/Debug/skse64_1_6_***.pdb`
  - `skse64/build/skse64_loader/Debug/skse64_loader.exe`
  - `skse64/build/skse64_loader/Debug/skse64_loader.pdb`
  - `skse64/build/skse64_steam_loader/Debug/skse64_steam_loader.dll`
  - `skse64/build/skse64_steam_loader/Debug/skse64_steam_loader.pdb`
1. Download [Address Library](https://www.nexusmods.com/skyrimspecialedition/mods/32444) mod and install

### 5. (Optional) Attach debuger in Visual Studio 

1. Make sure you follow step `4.`
1. TODO...
