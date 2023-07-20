# Installing Windows 11 on a Mac to export to an AWS environemnt

## The most tedious,monitinous, mind numbing thing you can possibly come across

## Instructions

1. Find the edition of Windows you want to install on UUP dump. Once you downloaded and extracted the installer creator, you need to run `uup_download_macos.sh` from Terminal to generate the ISO. (Read "troubleshooting" if you are having issues here.)
2. Make sure you select `arm64` if you are on Apple Silicon and `amd64` if you are on Intel!
3. Open UTM and click the "+" button to open the VM creation wizard.
4. Select "Virtualize".
5. Select "Windows".
6. Make sure "Import VHDX Image" is unchecked and "Install Windows 10 or higher" is checked. Also, make sure "Install drivers and SPICE tools" is checked. Press "Browse" and select the ISO you built in step 1.
7. Pick the amount of RAM and CPU cores you wish to give access to the VM. Press "Next" to continue.
8. Specify the maximum amount of drive space to allocate. Press "Next" to continue.
9. If you have a directory you want to mount in the VM, you can select it here. Alternatively, you can skip this and select the directory later from the VM window's toolbar. The shared directory will be available after installing SPICE tools (see below). Press "Next" to continue.
10. Press "Save" to create the VM. Wait for the guest tools to finish downloading and press the Run button to start the VM.
11. Follow the Windows installer. If you have issues with the mouse, press the mouse capture button in the toolbar to send mouse input directly. Press Control+Option together to exit mouse capture mode. Sometimes, due to driver issues, you can enter and exit capture mode and the mouse cursor works normally again.

### Installing the Microsoft Store and UWP apps (optional)

*WIP*
Check this issue for more information.

## Troubleshooting

**Cannot run `uup_download_macos.sh`**

In Terminal, go to the directory containing `uup_download_macos.sh`

```bash
$ cd path/to/extracted/files
Make sure that uup_download_macos.sh is executable by running

bash
 
$ chmod +x uup_download_macos.sh
Make sure you have the prerequisites installed

bash
 
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
$ brew tap sidneys/homebrew
$ brew install aria2 cabextract wimlib cdrtools sidneys/homebrew/chntpw
Then you can run uup_download_macos.sh

bash
 
$ ./uup_download_macos.sh
Extract from https://docs.getutm.app/guides/windows/#downloads

```

Potential troubleshooting commands for the troubleshooting

```bash
brew tap minacle/chntpw
brew install minacle/chntpw/chntpw
```

### Converting to an AWS friendly format (vhdx)


Unless you change this during the installation of UTM, the directory we want to be looking for is
markdown
 
## UTM VM Directory Navigation

1. Change to the UTM documents directory:
```bash
cd ~/Library/Containers/com.utmapp.UTM/Data/Documents/
List the contents of the documents directory:

```bash 
ls
KaliLinux2022.3.utm  Public  Windows.utm
Change to the Windows UTM directory:



 ```bash
cd Windows.utm
List the contents of the Windows UTM directory:

 ```bash
 
ls
Data  config.plist
Change to the Data directory:

 ```bash

cd Data
List the contents of the Data directory:

 ```bash

ls
4BC1CFCF-9D29-4D07-B808-126903960273.qcow2  efi_vars.fd

$ ls
4BC1CFCF-9D29-4D07-B808-126903960273.qcow2 4BC1CFCF-9D29-4D07-B808-126903960273.vhdx efi_vars.fd

$ qemu-img convert -f 4BC1CFCF-9D29-4D07-B808-126903960273.qcow2 -O vhdx 4BC1CFCF-9D29-4D07-B808-126903960273.vhdx
qemu-img: Must specify image file name

$ qemu-img convert -f qcow2 4BC1CFCF-9D29-4D07-B808-126903960273.qcow2 -O vhdx 4BC1CFCF-9D29-4D07-B808-126903960273.vhdx
qemu-img: 4BC1CFCF-9D29-4D07-B808-126903960273.vhdx: error while converting vhdx: Could not create '4BC1CFCF-9D29-4D07-B808-126903960273.vhdx': Permission denied

$ sudo qemu-img convert -f qcow2 4BC1CFCF-9D29-4D07-B808-126903960273.qcow2 -O vhdx 4BC1CFCF-9D29-4D07-B808-126903960273.vhdx
Password: d

$ ls
4BC1CFCF-9D29-4D07-B808-126903960273.qcow2 4BC1CFCF-9D29-4D07-B808-126903960273.vhdx efi_vars.fd


joshuawatkins@Joshuas-MacBook-Pro Data % sudo mv 4BC1CFCF-9D29-4D07-B808-126903960273.vhdx ~/Documents/GitHub/Windows-11-Professional.vhdx


joshuawatkins@Joshuas-MacBook-Pro GitHub % ls
Windows-11-Professional.vhdx


