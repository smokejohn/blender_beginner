

######################
Installation and Setup
######################


***************
Where to get it
***************


Blender Long Term Support LTS (Stable)
======================================
Download the **Stable LTS version of blender** for Linux, Windows or Mac OS at
the following url:

`Blender Stable 2.8`_
    **Current long term support version**

The Blender Stable can be installed via the Microsoft Windows Store on Windows
machines, via Steam on Mac OS, Windows and Linux (not recommended) or via the
Canonical Snap Store on Linux. If you install Blender this way you will get 
automatic updates.

Alternatively you can also download a binary package for Linux, Mac OS and choose
between a binary package or msi-installer on Windows. Do this if you want to be
in control of the update cycle and want to choose when and if you update.


Blender Latest and Experimental
===============================
.. note:: 
    If you are in need of one of the features only avaiable in the newer builds
    of Blender like the *Latest Release version* or the *Experimental Version*
    use one of the links below:

`Blender Latest 2.9`_
    Latest release with the newest features, might have some bugs

`Blender Experimental 2.91`_
    Experimental version, might be unstable, use to try latest features

.. _Blender Stable 2.8: https://www.blender.org/download/lts
.. _Blender Latest 2.9: https://www.blender.org.download/
.. _Blender Experimental 2.91: https://builder.blender.org/download/


*************************************
Installation and Application Settings
*************************************


Windows
=======
Installation depends on whether you aquired an **Installer (.exe, .msi)** or a 
**binary package (.zip, .rar)** from the blender website.


Installer
---------
Start the installer (\*.exe, \*.msi) and follow the instructions in the Installer
until the end. You should now be able to start blender via the Windows Startmenu.


Binary Package
--------------
Binary packages are often either .rar or .zip-files. Unzip or unrar using an
extraction application like `winrar <https://www.win-rar.com>`_ or 
`7-zip <https://www.7-zip.org/>`_. Once unpacked the folder contains the Blender
binary executable and all needed files. You can move the folder to a location
of your choosing on your harddrive. If you want it to show up in the Startmenu
you need to add it yourself.


.. note::
    Binary Packages are great if you want to have multiple versions of blender
    installed right next to each other!


Application Settings location
-----------------------------
Application Settings contain your userpreferences, bookmarks, scripts and addons

Location:
    C:\\Users\\[user]\\AppData\\Roaming\\Blender Foundation\\[version]\\

Linux
=====
Installation depends on which way you choose to install Blender. Some Linux
distributions have the latest Blender builds in their package manager
repositories (e.g. Ubuntu, Fedora, Arch/Manjaro in AUR). This is the most
comfortable way to install Blender on Linux. But if it is not in your in
your package managers repository or the version is ancient you have other
options.


Binary Package
--------------
Binary packages on linux are often .zip, or .tar-archives. Unzip or untar using
an extraction application for the archive (tar, unzip, zip) or your distros
file browser. Once unpacked the folder contains the Blender binary executable
and all needed files. You can move the folder to a location of your choosing on
your harddrive. If you want it to show up in your Application menu add the
included blender.desktop file to the ~/.local/share/applications/ folder. Make
sure the exec path inside the desktop file points to the Blender binary.


Snap
----
If you have snap installed on your distro you can visit `Canonical's snapcraft
store <https://snapcraft.io/blender>`_ to install Blender and have it update
automatically.


Application Settings location
-----------------------------
Application Settings contain your userpreferences, bookmarks, scripts and addons

Location:
    ~/.config/blender/[version]/

Mac OS
======

Most of the time you will get a .dmg disk image file. Sometimes you will get a .pkg
installer or a .dmg file will contain a .pkg-installer.

.. warning::
    If you are on Mac OS you will not be able to render with Cycles render engine
    using your graphical processing unit (GPU) due to Apple removing OpenCL 
    support from their Operating System. Only CPU rendering will be supported
    for Cycles but everything else will work just fine.


Disk Image File
---------------
Drag and drop the .dmg-file into /Applications to install it and enter your
user password if you are prompted for it.

PKG Installer
-------------
Double click the .pkg-file to start the Installation Wizard. Follow it's instruction
to the end and you will have successfully installed Blender.


Application Settings location
-----------------------------
Application Settings contain your userpreferences, bookmarks, scripts and addons

Location:
    ~/Library/Application Support/Blender/[version]/

