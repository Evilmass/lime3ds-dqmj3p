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
