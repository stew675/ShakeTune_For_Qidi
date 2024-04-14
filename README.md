# ShakeTune For Qidi Printers

## Introduction

This a precompiled version of Klippain Shaketune made for easy installation on Qidi 3D Printers.  This package includes
a number of bug fixes and minor packaging optimizations for the stock Qidi environment.

Suitable Printers are: Qidi X-Smart 3, Qidi X-Plus 3, Qidi X-Max 3, Qidi Q1 Pro

The Original Klippain Source code can be found here: https://github.com/Frix-x/klippain-shaketune/tree/main

The Klippain Shaketune was pulled fresh as at April 12th 2024.

This package also includes a pre-compiled version of Python 3.12.3 built from the source code that is available here: https://github.com/python/cpython/tree/v3.12.3

## Installation instructions

This guide assumes you are comfortable working within the login shell on Qidi printers.  This guide also assumes
that your printer can access the internet, although if it cannot, the tarball files can be loaded onto a USB
drive, and copied from that drive on the printer.

Because Klippain demands an extensive set of libraries, as well as a modern version of Python, this installation
is quite large at ~700MB.  We also need to download the package tarballs which themselves are 255MB in size.

**Please ensure that there is at least 1GB of free disk space on the /home/mks partition**

1. First ssh into your printer, using Putty if on Windows
  * ssh <your printer's IP address>
  * Username: **mks**
  * Password: **makerbase**
  * If you had previously changed the password for the **mks** user, then of course use that instead
2. Then type in the following commands:
```
  cd /home/mks
  wget https://github.com/stew675/ShakeTune_For_Qidi/releases/download/v1.0.0/klippain-for-qidi.tgz
  wget https://github.com/stew675/ShakeTune_For_Qidi/releases/download/v1.0.0/python-3-12-3.tgz
  tar xvzf klippain-for-qidi.tgz
  tar xvzf python-3-12-3.tgz
  rm klippain-for-qidi.tgz python-3-12-3.tgz
```
3. In the FluiddUI, edit your **printer.cfg** file
..* Near the top of the file where you see the _include_ section, add the following line
..* **[include K-ShakeTune/*.cfg]**
..* Now click the **Save & Restart** button at the top
4. The installation is complete.  You are now done.

## What did that installation just do?

### python-3-12-3.tgz

This creates a new directory called **python-3.12.3** which is a mostly complete standalone Python 3.12.3 environment.
This version of Python does not appear to be compatible with Qidi's stock version 3.7 of Python, which is why I chose
to install it as a separate package.  If you wish to play around with it, add the following directory to your PATH
environment variable:
```
/home/mks/python-3.12.3/bin
```

### klippain-for-qidi.tgz

This creates a new directory called **klippain_shaketune** which contains the shaketune scripts and associated python
environment that the klippain utility requires.

This also installs a new gcode command called `gcode_shell_command` into the Qidi Klipper environment by creating the
following file:
```
/home/mks/klipper/klippy/extras/gcode_shell_command.py
```

That command allows for gcode files to call shell scripts, which is the mechanism that Klippain uses to invoke the
Python scripts that it uses to do its job

Additionally, the tarball also does the following

1. Creates a symlink from `/home/mks/klipper_config/K-ShakeTune` to `/home/mks/klippain_shaketune/K-Shaketune`
  * This allows for Klipper to be able to find the Klippain config files and scripts
2. Creates the directory `/home/mks/klipper_config/K-ShakeTune_results` which is where Klippain will store the various output graphs, which are able to be easily accessed from the FluiddUI in the `Configuration` tab

## How to Uninstall and delete Klippain ShakeTune (and Python 3.12.3)

Open an ssh shell onto your printer and run the following commands:

```
cd
rm -rf klippain_shaketune python-3.23.3 klipper_config/K-ShakeTune_results
rm -f klipper_config/K-ShakeTune klipper/klippy/extras/gcode_shell_command.py
```

Now edit your **printer.cfg** file and remove the  **[include K-ShakeTune/*.cfg]** line, then click **Save & Restart**

That's it.  Klippain ShakeTune for Qidi will now be completely purged from your printer.

## Klippain ShakeTune Documentation

Documentation for Klippain can be found on the main Klippain GitHub page: [https://github.com/Frix-x/klippain-shaketune](https://github.com/Frix-x/klippain-shaketune/tree/main/docs)


