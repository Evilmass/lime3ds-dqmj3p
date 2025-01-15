This is a fork of the source code of the final version of Lime3DS, utilizing the core timing prior to Citra nightly-1544, to enhance performance on Dragon Quest Monster Joker 3 Professional (performance may degrade on many other games).

It is also beneficial if, for some reason, you cannot run nightly-1543 (for example, if you use an AMD GPU that no longer supports drivers compatible with nightly-1543).

Useful information:

-   [Citra Legacy Builds info and changes - Web Archive](https://web.archive.org/web/20230603005840/https://citra-emu.org/wiki/citra-legacy-builds/#last-build-before-the-core-timing-rewrite)
-   [Citra Pull Request #4913 (the one that changed core timing) - Web Archive](https://web.archive.org/web/20230212174257/https://github.com/citra-emu/citra/pull/4913)

This fork was inspired by Slashaim's fork of the old Citra code.

-   [Slashaim's Citra Fork](https://github.com/Slashaim/citra-dqmj3pro?tab=readme-ov-file)

To build this project, clone the repo using the following script

```sh
git clone --recursive https://github.com/Lurpigi/lime3ds-dqmj3p
```

And refer to the detailed instructions provided in the following wiki:

-   [Building from Source](https://github.com/azahar-emu/azahar/wiki/Building-From-Source)

---

# info from ReadMe Lime3DS

<h1 align="center">
  <br>
  <a href="[https://github.com/Lime3DS]"><img src="https://raw.githubusercontent.com/Lime3DS/Lime3DS/1b1c4f29d4280c750702459fd9a6ada539a4e9a9/dist/lime.svg" alt="Lime3DS" width="200"></a>
  <br>
  <b>Lime3DS</b>
  <br>
</h1>

<b>Lime3DS</b> is a project which aims to revive and continue work on Citra, a popular open-source Nintendo 3DS emulator which ceased development.

#### Windows Version Differences

There is no emulation specific difference between the MSVC and MSYS2 versions of Lime3DS, they are just two different compilers used to create a Lime3DS executable. However, there are a few functional differences:

-   MSVC generates a smaller file
-   Microsoft developed [MSVC](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist) and is closed source while [MSYS2](https://www.msys2.org/) is open-source
-   MSVC requires the installation of [Microsoft Visual C++ runtime](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist), if not already installed, which can require a restart to finish the install. If you have issues with the Microsoft Visual C++ runtimes, you should try the MSYS2 install
-   There have been reports where MSVC has not worked while MSYS2 does

# Compatibility Reporting

Reports for game compatibility can be made here: https://github.com/Lime3DS/compatibility-list

Please ensure that you have read the contributing document before submitting a report.

# Minimum Requirements

Below are the minimum requirements to run Lime3DS:

### Desktop

```
Operating System: Windows 10 (64-bit), MacOS Ventura, or modern 64-bit Linux
CPU: x86-64 (64-bit) CPU. Single core performance higher than 1,800 on Passmark
GPU: OpenGL 4.3 or Vulkan 1.1 support
Memory: 2GB of RAM. 4GB is recommended
```

### Android

```
Operating System: Android 9.0+
CPU: Snapdragon 835 SoC or better
GPU: OpenGL ES 3.2 or Vulkan 1.1 support
Memory: 2GB of RAM. 4GB is recommended
```

# Build Guide (If the link above breaks)

Firstly, clone the Lime3DS repository using the following command:

```
git clone --recursive https://github.com/Lurpigi/lime3ds-dqmj3p
```

After this has finished, use the following instructions depending on your operating system:

<details>
<summary><h2>Windows</h2></summary>

<details>
<summary><h4>⠀⠀MSVC</h4></summary>

Ensure that the following are installed:
- [Visual Studio 2022](https://visualstudio.microsoft.com/) (Install C++ Support)
- [CMake GUI](https://cmake.org/)

Then, follow these instructions:
- Open the CMake GUI Application and point it to the Lime3DS directory
- Use the preexisting build/ directory or tell CMake to make one
- Click the configure button and choose Visual Studio 17 2022 with x64 for the optional platform
  - If you get errors like "XXX does not contain a CMakeLists.txt file", it means you did not use the --recursive flag when cloning the repo.
  - Please run `git submodule update --init --recursive` to get the submodules
- Click Generate to create the project files
- Open the solution file in Visual Studio 2022, which is located in the build folder
- Depending on which frontend (SDL2 or Qt) you want to build or run, select "lime" or "lime-qt" in the Solution Explorer, right click and "Set as Starup Project"
- Select the appropriate build type, Debug for debug purposes or Release for performance (if in doubt, choose the latter)
- Press F5 or select Build → Rebuild Solution in the menu
</details>

<!---------------------------------------------------------------------------------------------------------------->
<details>
<summary><h4>⠀⠀MSYS2</h4></summary>

First, ensure that [MSYS2](https://www.msys2.org/) is installed.

Then, follow these instructions:

- Open the "MSYS2 Clang64" (clang64.exe) shell inside the Lime3DS directory
- Download and install all dependencies using: `pacman -S mingw-w64-clang-x86_64-{gcc,qt6,cmake} make git`
- Make a build directory: `mkdir build && cd build`
- Make CMake files: `cmake -DCMAKE_BUILD_TYPE=Release ..`
  - If you wish to build Lime3DS without the Qt GUI, `pass -DENABLE_QT=no to CMake`.
- Make the executable: `cmake --build . -- -j$(nproc)`
- You can run the exe from command line with: `./bin/lime-qt.exe`
</details>
</details>

<!---------------------------------------------------------------------------------------------------------------->
<details>
<summary><h2>MacOS</h2></summary>

Ensure that the following are installed:
- CMake (`brew install cmake`)
- A recent version of Xcode and the Xcode command line tools

Then, follow these instructions:
- Make the build directory: mkdir build && cd build
- Make CMake files for your machine's architecture:
  - ARM: `cmake .. -DCMAKE_OSX_ARCHITECTURES="arm64"`
  - x86: `cmake .. -DCMAKE_OSX_ARCHITECTURES="x86_64"`
- Make executable: `make -j$(sysctl -n hw.logicalcpu)`
- Make a distributable executable with: `make bundle`
</details>

<!---------------------------------------------------------------------------------------------------------------->
<details>
<summary><h2>Linux</h2></summary>

Ensure that the following are installed:
- SDL2
  - Deb: sudo apt install libsdl2-dev
  - Arch: pacman -S --needed sdl2
  - Fedora: sudo dnf install SDL2-devel
  - OpenSUSE: zypper in libSDL2-devel
- OpenSSL (Optional)
  - Deb: sudo apt install libssl-dev
  - Arch: pacman -S --needed openssl-1.0
  - Fedora: sudo dnf install openssl-devel
  - OpenSUSE: zypper in openssl-devel
- Qt 6.2+
  - Deb: sudo apt install qt6-base-dev qt6-base-private-dev qt6-multimedia-dev
  - For Translation Support: apt install qt6-l10n-tools qt6-tools-dev qt6-tools-dev-tools
  - For WrapOpenGL Errors: apt install libgl-dev
  - Arch: pacman -S --needed qt6-base qt6-multimedia qt6-multimedia-ffmpeg
  - You also need a multimedia backend: qt6-multimedia-ffmpeg or qt6-multimedia-gstreamer
  - Fedora: sudo dnf install qt6-qtbase-devel qt6-qtbase-private-devel qt6-qtmultimedia-devel
  - OpenSUSE: zypper in qt6-base qt6-multimedia
- PortAudio
  - Deb: sudo apt install libasound-dev
  - Fedora: sudo dnf install portaudio-devel
  - OpenSUSE Leap 15: zypper in portaudio-devel
  - OpenSUSE Tumbleweed: zypper in portaudio-devel
- XORG
  - Deb: sudo apt install xorg-dev libx11-dev libxext-dev
  - Fedora: sudo dnf install xorg-x11-server-devel libX11-devel libXext-devel
  - OpenSUSE Leap 15: zypper in xorg-x11-util-devel libX11-devel libXext-devel
  - OpenSUSE Tumbleweed: zypper in xorg-x11-util-devel libX11-devel libXext-devel
- JACK Audio Connection Kit
  - Deb: sudo apt install jackd
  - Fedora: sudo dnf install jack-audio-connection-kit-devel
  - OpenSUSE Leap 15: zypper in libjack-devel
  - OpenSUSE Tumbleweed: zypper in libjack-devel
- PipeWire
  - Deb: sudo apt install libpipewire-0.3-dev
  - Fedora: sudo dnf install pipewire-devel
  - OpenSUSE Leap 15: zypper in pipewire-devel
  - OpenSUSE Tumbleweed: zypper in pipewire-devel
- sndio (Optional)
  - Deb: sudo apt install libsndio-dev
  - Fedora: sudo dnf -y copr enable andykimpe/shadow && sudo dnf -y install sndio
  - OpenSUSE Leap 15: zypper in sndio-devel
  - OpenSUSE Tumbleweed: zypper in sndio-devel
- Gnome ESound (Optional)
  - Deb: echo "esound require build use source code https://download.gnome.org/sources/esound/"
  - Fedora: sudo dnf install esound-devel
  - OpenSUSE Leap 15: zypper in libesd0-devel
  - OpenSUSE Tumbleweed: zypper in libesd0-devel
- Compiler (You only need one of these)
  - GCC 11.0+
    - Deb: apt install build-essential
    - Arch: pacman -S --needed base-devel
    - Fedora: dnf install gcc-c++
    - OpenSUSE: zypper in gcc-c++
  - Clang 18.0+
    - Deb: apt install clang clang-format libc++-dev
    - Arch: pacman -S --needed clang, libc++ is in the AUR. Use pacaur or yaourt to install it.
    - Fedora: dnf install clang libcxx-devel
    - OpenSUSE: zypper in clang
- CMake 3.22+
  - Deb: apt install cmake
  - Arch: pacman -S --needed cmake
  - Fedora: dnf install cmake
  - OpenSUSE: zypper in cmake extra-cmake-modules

Then, enter one of the following depending on your compiler:
### GCC
```
mkdir build
cd build
cmake ../
cmake --build . -- -j"$(nproc)"
sudo make install (optional)
```
### Clang
```
mkdir build
cd build
cmake .. -DCMAKE_CXX_COMPILER=clang++ \
    -DCMAKE_C_COMPILER=clang \
    -DCMAKE_CXX_FLAGS="-O2 -g -stdlib=libc++"
cmake --build . -- -j"$(nproc)"
sudo make install (optional)
```
If you get a weird compile error related to std::span conversions, make sure you are using clang and libc++ 15 or up. This is an issue with libc++ 14.

### Installing newer Qt Version
If your distribution’s version of Qt is too old, there are a few places you may be able to find newer versions.

This Ubuntu PPA contains backports of Qt 6 to various older versions: https://launchpad.net/~savoury1/+archive/ubuntu/qt-6-2
This unofficial CLI installer allows downloading and installing the latest first-party builds of Qt to your system
(whether it works against your distribution may vary): https://github.com/miurahr/aqtinstall

</details>

<!---------------------------------------------------------------------------------------------------------------->
<details>
<summary><h2>Android</h2></summary>

Firstly, ensure that [Android Studio](https://developer.android.com/studio) is installed with NDK and CMake support enabled in the SDK tools.

Then, follow these instructions:
- Start Android Studio and on the startup dialog select 'Open'.
- Navigate to the `Lime3DS/src/android` directory and click on 'Ok'
- Build the project with 'Build' > 'Make Project' or run it on an Android device with 'Run' > 'Run 'app''
</details>

<!---------------------------------------------------------------------------------------------------------------->
<details>
<summary><h2>OpenBSD (Unofficial)</h2></summary>

OpenBSD, and by extension these instructions, are not officially supported. YMMV.

Firstly, install the required packages:
```
pkg_add cmake sdl2 qtbase
```
Then, follow these instructions:
- Make the build directory: `mkdir build && cd build`
- Export the Qt directory: `export Qt5_DIR=/usr/local/lib/qt5/cmake/Qt5`
- Make CMake files: `cmake -DCMAKE_CXX_FLAGS='-I/usr/local/include -O2' -DCMAKE_EXE_LINKER_FLAGS='-z wxneeded' ..`
- Make the executable: `make`

</details>

