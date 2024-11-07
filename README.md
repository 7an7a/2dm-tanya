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

## Installing Python 3


Based on macOS `Catalina 10.15 release notes`_, use of Python 2.7 is not recommended and Python 2.7 is not included by default in future versions of macOS. Check what Python you currently have

```
python --version
```

If the output is like ``Python 2.7.17``, your default interpreter is Python 2.7. If so, also check if Python 3 is not already installed on your computer


```
  python3 --version
```


If the above command returns an error, it means Python 3 is not installed.


Below is an overview of the steps to install Python 3.


  - Installing with [HomeBrew](https://brew.sh/) can be done as follows

```
  brew install python3
```

 **Step 2. Get ESP-IDF**
 
To build applications for the {IDF_TARGET_NAME}, you need the software libraries provided by Espressif in [ESP-IDF repository](https://github.com/espressif/esp-idf)

To get ESP-IDF, navigate to your installation directory and clone the repository with ``git clone``, following instructions below specific to your operating system.

Open Terminal, and run the following commands:


```
mkdir -p ~/esp
cd ~/esp
git clone --recursive https://github.com/espressif/esp-idf.git
```
ESP-IDF is downloaded into ``~/esp/esp-idf``.


**Step 3. Set up the Tools**

Aside from the ESP-IDF, you also need to install the tools used by ESP-IDF, such as the compiler, debugger, Python packages, etc, for projects supporting {IDF_TARGET_NAME}.

.. code-block:: bash

    cd ~/esp/esp-idf
    ./install.sh {IDF_TARGET_PATH_NAME}













    
