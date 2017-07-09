# Pulse Connect Secure Client
This is a modified version for Manjaro Linux based on Keith Miyake's Arch version (https://github.com/kaymmm/pulseconnectsecure-arch). Thanks to Keith Miyake.

## Description

Manjaro package for the Pulse Connect Secure client.

## Installation

git clone this repository or download the source, then cd into the source directory and run ```makepkg -ci```

## Updated by Junli on 07/09/2017
I did a few things to make it work in Manjaro Linux.
- Downloaded the pulse-8.2R5.i386.rpm from the web, because the the original link is expired. And edited the PKGBUILD file accordingly.
- Removed dependency requirements in the PKGBUILD file for webkitgtk, xulrunner, lib32-libsoup and lib32-gtk3, because I only used the command line options.
- Replaced the "arch-release" with "manjaro-release" in the two patch files, got the new md5sum with commands `md5sum PulseClient.patch` and `md5sum ConfigurePulse.patch`, and updated the PKGBUILD file.
- That is it. Then just run `makepkg -ci` because I already have all the dependencies installed. Just ignore this notice in the installation:
```sh
Please execute below commands to install missing dependent packages 
pacman -S webkitgtk
pacman -S xulrunner
```
- For UC-Davis users, run this command to connect `/opt/pulse/PulseClient.sh -h vpn.library.ucdavis.edu -u yourUSERNAME -r Library`. Press **Ctl-C** to end the VPN.
- You can use command `route` to check whether you are in VPN connection. You may need to restart your browser to make it aware of the VPN.

-----

# Below are the Keith Miyake's help information

## Usage

### Start the VPN Client

To run the client (from the official documentation): 

```sh
/opt/pulse/PulseClient.sh -h <hostname/IP> -u <VPN username> [-p <VPN password>] [-r <realm>] [-U <PCS signinurl>] [-y <proxy IP/hostname>] [-z <proxy port>]
```
__Note:___ The client does not provide feedback when a connection has been successfully established. Use Ctl-C to end it.

You should leave out the ```-p``` (password) option so that it prompts you to enter the password securely so that your password doesn't end up in cleartext in your command history.

If you don't include the realm, it will default to Users.

### Stop the VPN Client

To kill the VPN client:

```sh
/opt/pulse/PulseClient.sh -K
```

## Package Info

Built from an RPM found on the UC Davis library website since Pulse doesn't make the client publicly available.

This package will only install the command-line tool since the pulseUi is broken on x64 systems. I tried to get it to work correctly, but it depends on lib32-webkitgtk (and several other 32-bit libs), which is no longer available on AUR and wouldn't build successfully after numerous attempts.

There are some extra deps that don't need to be there, but I haven't tried uninstalling them to see which ones will break it. webkitgtk is definitely not needed since it's only used for the broken UI.

