***********
Get Started
===========
***********
This document is intended to help you set up the software development environment for the hardware based on the {IDF_TARGET_NAME} chip by Espressif. After that, a simple example will show you how to use ESP-IDF (Espressif IoT Development Framework) for menu configuration, then for building and flashing firmware onto an {IDF_TARGET_NAME} board.


## What You Need


**Herdware**
* An **{IDF_TARGET_NAME}** board.
* **USB cable** - USB A / micro USB B.
* **Computer** running Windows, Linux, or macOS.

*note*

Currently, some of the development boards are using USB Type C connectors. Be sure you have the correct cable to connect your board!

**Software**

To start using ESP-IDF on **{IDF_TARGET_NAME}**, install the following software:

* **Toolchain** to compile code for {IDF_TARGET_NAME}
* **Build tools** - CMake and Ninja to build a full **Application** for {IDF_TARGET_NAME}
* **ESP-IDF** that essentially contains API (software libraries and source code) for {IDF_TARGET_NAME} and scripts to operate the **Toolchain**

## Installation

**Standard Toolchain Setup for macOS**

This is a detailed roadmap to walk you through the installation process.

**Step 1. Install Prerequisites**

ESP-IDF uses the version of Python installed by default on macOS.

Install CMake & Ninja build:

  - If you have [HomeBrew](https://brew.sh/) you can run:

```
brew install cmake ninja dfu-util
```
Otherwise, consult the [CMake](https://cmake.org/)and [Ninja](https://ninja-build.org/)home pages for macOS installation downloads.

It is strongly recommended to also install ccache_ for faster builds. 

  - If you have[HomeBrew](https://brew.sh/), this can be done via ``brew install ccache``

 *note*

 
   If an error like this is shown during any step

     xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools), missing xcrun at: /Library/Developer/CommandLineTools/usr/bin/xcrun

   Then you need to install the XCode command line tools to continue. You can install these by running ``xcode-select --install``.
    

