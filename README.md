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


```
cd ~/esp/esp-idf
./install.sh esp32
```

The above commands install tools for {IDF_TARGET_NAME} only. If you intend to develop projects for more chip targets then you should list all of them and run for example:


```
cd ~/esp/esp-idf
./install.sh esp32,esp32s2
```
In order to install tools for all supported targets please run the following command:

```
cd ~/esp/esp-idf
./install.sh all
```

*note*
   For macOS users, if an error like this is shown during any step
```
     <urlopen error [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed: unable to get local issuer certificate (_ssl.c:xxx)
```
   You may run ``Install Certificates.command`` in the Python folder of your computer to install certificates. For details, see [Download Error While Installing ESP-IDF Tools](https://github.com/espressif/esp-idf/issues/4775)


**Step 4. Set up the Environment Variables**

The installed tools are not yet added to the PATH environment variable. To make the tools usable from the command line, some environment variables must be set. ESP-IDF provides another script which does that.

In the terminal where you are going to use ESP-IDF, run:

```
. $HOME/esp/esp-idf/export.sh
```

or for fish (supported only since fish version 3.0.0):
```
. $HOME/esp/esp-idf/export.fish
```

Note the space between the leading dot and the path!

If you plan to use esp-idf frequently, you can create an alias for executing ``export.sh``:

1.  Copy and paste the following command to your shell's profile (``.profile``, ``.bashrc``, ``.zprofile``, etc.)

```
alias get_idf='. $HOME/esp/esp-idf/export.sh'
```

2.  Refresh the configuration by restarting the terminal session or by running ``source [path to profile]``, for example, ``source ~/.bashrc``.

*More detailed steps are*
1. Getting what type of shell your Macbook is running

Normally everyone's computer runs:

```
echo $SHELL
```
it gonna shows ``/bin/zsh``

then runs：

```
vi ～/.zprofile
```

To edit, you need to press the I key，run：


```
alias get_idf='. $HOME/esp/esp-idf/export.sh'
```
press esc, and run:


```
:wq
```
At this point, run the command again to verify that the command line you just entered `` alias get_idf='. $HOME/esp/esp-idf/export.sh' ``is still there.



```
alias get_idf='. $HOME/esp/esp-idf/export.sh'
```


















Now you can run ``get_idf`` to set up or refresh the esp-idf environment in any terminal session.

Technically, you can add ``export.sh`` to your shell's profile directly; however, it is not recommended. Doing so activates IDF virtual environment in every terminal session (including those where IDF is not needed), defeating the purpose of the virtual environment and likely affecting other software.

Step 5. First Steps on ESP-IDF
Tip: Updating ESP-IDF
It is recommended to update ESP-IDF from time to time, as newer versions fix bugs and/or provide new features. Please note that each ESP-IDF major and minor release version has an associated support period, and when one release branch is approaching end of life (EOL), all users are encouraged to upgrade their projects to more recent ESP-IDF releases, to find out more about support periods, see :doc:`ESP-IDF Versions <../versions>`.

The simplest way to do the update is to delete the existing esp-idf folder and clone it again, as if performing the initial installation described in :ref:`get-started-get-esp-idf`.

Another solution is to update only what has changed. :ref:`The update procedure depends on the version of ESP-IDF you are using <updating>`.

After updating ESP-IDF, execute the Install script again, in case the new ESP-IDF version requires different versions of tools. See instructions at :ref:`get-started-set-up-tools`.

Once the new tools are installed, update the environment using the Export script. See instructions at :ref:`get-started-set-up-env`.

Related Documents
:doc:`establish-serial-connection`
Eclipse Plugin
VSCode Extension
:doc:`../api-guides/tools/idf-monitor`
.. toctree::
    :hidden:
    :maxdepth: 1

    establish-serial-connection
    flashing-troubleshooting




















    
