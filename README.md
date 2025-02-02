# PLAY-BOX64-EMULATOR-
Box64Droid
telegram discord

Box64Droid is a project with scripts that automate installing preconfigured rootfs with Box64, Box86, Wine, DXVK, D8VK on Android. Originally was a fork of Box4Droid with Box64.
# INSTALL
News about the project are published on the Telegram channel.
The project site is available here.
Installation instructions
Install Termux, Termux-x11 and Termux:Widget.
In Termux, run the Box64Droid install command, select need version (i recommend native) and wait until it's installed: 'curl -o install https://raw.githubusercontent.com/Ilya114/Box64Droid/main/installers/install.sh && chmod +x install && ./install'
After the installation is completed, run 'box64droid --start'. The script will start Termux-X11 and show the start menu.
To use Input Bridge, install 0.1.9 apk and then simply run the app on Android and in Wine from the start menu.
Launch via homescreen using Termux:Widget (native version)
You can launch and update Box64Droid via start menu, just create Termux:Widget widget and you will see these options

System requirements
Adreno 610+ (Other GPUs are supported by VirGL, but many games might not work)
Android 12+ (non-root, VirGL version), Android 10+ (root version), Android 9+ (native version)
64-bit Android
You also need ~4,2GB (for root version), 4,5GB (for non-root version) or ~3,3GB (for VirGL version) worth of free space for the installation to run without problems.
To increase performance and stability, use the root version (root access required) or the native version (less stable but offers the same performance as the root version).

Configuring
You can choose to use environment variables; there are three files: DXVK_D8VK.conf, Box64Droid.conf, and DXVK_D8VK.conf. These files are created and found in the /sdcard/Box64Droid/ folder after the first Box64Droid run.
The Box64Droid.conf file includes configurations for rootfs, Box86, Box64, and Wine. You can utilize the Box86 and Box64 environment variables; you can find more information about them here and here. You can add as many variables as needed.
The DXVK_D8VK_HUD.conf file is intended for using environment variables related to DXVK_HUD.
The DXVK_D8VK.conf file is intended for using environment variables related to dxvk.
Known issues
Very fast "install" (which really failed due a Termux update packages process failed). Clear Termux data will resolve this issue.
Android 12+ may terminate Termux, displaying [Process completed (signal 9) - press Enter]. To resolve this, execute the following command in from your PC (you need plaform-tools and enabled ADB debugger in phone): adb shell "/system/bin/device_config put activity_manager max_phantom_processes 2147483647".
Winetricks takes a long time to run when Proton is installed (non-root version).
Instructions on how to mount SD-card external HDD/SSD (chroot version only)
If you want to mount an SD card or an external drive (HDD/SSD), you need to add the mountpoint manually. Follow these steps:

Mount the drive onto the phone storage:
For an SD card, navigate to /storage and check the folders (using sudo ls), for example, 8D3E-2B7K.
For external drives, navigate to /mnt/media_rw and check for a folder like C3G3H6B8A56212H7.
Mount the drive into the chroot envrionment:
Type nano $PREFIX/bin/box64droid and add the mount command before the sudo chroot login ... line: sudo mount --bind /mnt/media_rw/drivename (or /storage/sdcardname) $ROOTFSPATH/needfolder.
You need to manually create needfolder in the ~/ubuntu folder by using sudo mkdir foldername.
Applications and scripts which were used in Box64Droid
Termux-app - GPLv3 license
Box64 by ptitseb - MIT license
Box86 by ptitseb - MIT license
Wine Stable, Staging and Staging-tkg GPL-2.1 license (builded by Kron4ek by MIT License), Wine Proton by Valve (own license), Wine GE (using in Lutris)
Mesa - MIT, Khronos, SGI Free Software License B and Boost (permissive) licenses
Termux-x11 - GPL-3.0 license
DXVK - Zlib license
Proot-distro - GPL-3.0 license
Forked Mesa to work Turnip on Adreno 730 and 740
D8VK - Zlib license
DXVK-Async
DXVK-GPLAsync
WineD3D for Windows - GPL-2.0+ license
Winetricks
vkd3d-proton - LGPL v2.1 license
glibc-prefix - MIT license
Thanks to:
Herick75 - for providing patches that made compiling Mesa Turnip possible
Inguna87 - for start chroot fix for MIUI and Oxygen
Alfhashut - inspired me to try VirGL again and tried to help me with it
