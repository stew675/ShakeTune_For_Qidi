# ShakeTune_For_Qidi
A precompiled version of Klippain Shaketune made for easy installation on Qidi 3D Printers

Suitable Printers are: Qidi X-Smart 3, Qidi X-Plus 3, Qidi X-Max 3, Qidi Q1 Pro

This is a pre-compiled version of the project from here: https://github.com/Frix-x/klippain-shaketune/tree/main

The Klippain Shaketune was pulled fresh as at April 12th 2024.

This also includes a compiled version of Python 3.12.3 built from the source code here: https://github.com/python/cpython/tree/v3.12.3

I have made a number of bug fixes and modifications to the stock Klippain Shaketune scripts to make them suitable for
the somewhat unique Qidi Klipper environment.

Installation instructions:

* This guide assumes you are comfortable working within the login shell on Qidi printers
* Download the python 3.12.3 tarball, and the Klippain tarball
* Copy both to the /home/mks directory on your Qidi printer and extract them
* Edit your printer.cfg file and add the following line:

[include K-ShakeTune/*.cfg]

Somewhere near the top.

* Save your config and restart.
* That's it!  You're good to go

Documentation for Klippain can be found on the main Klippain GitHub Page
