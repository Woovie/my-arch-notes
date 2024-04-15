# My Arch Linux Notes

These are just some generalist notes about my own setup, issues I've had, configurations I've changed, software I like.

## Random knowledge

- `mkinitcpio` creates the /boot/ and /efi/ data
  - "mk" or make
  - "init" or initialization
  - "cpio" is a utility to create archives of files. It stands for "copy in, copy out"

## OS Packages needed

base linux linux-firmware sudo tmux ripgrep flameshot alacritty ark nvidia nvidia-settings xorg deluge rsync xorg-xinit flameshot steam dolphin noto-fonts{,-\*} openssh openssl alsa-scarlett-gui uv steam-devices firefox ulauncher 1password discord vial fuse2 plasma lvm2 networkmanager perl pcre pcre2

## Booting requirements

### LVM?

1. Edit `HOOKS` in `/etc/mkinitcpio.conf`, add `lvm2`
1. Run `mkinitcpio -P`

### NetworkManager

- Enable NetworkManager
- Disable `NetworkManager-wait-online`

## Nvidia-specific issues

### Flickering in KDE

To fix some flickering and performance issues mostly.

1. Generate `/etc/X11/xorg.conf` via running `sudo nvidia-settings` 
1. Click "X Server Display Configuration"
1. Click "Advanced..."
1. Check "Force Composition Pipeline" and "Force Full Composition Pipeline"
1. Click "Save to X Configuration File" and write it to the path predefined
1. Close the nvidia-settings UI, open the generated configuration with your favorite editor
1. Add this option under `Section "Device"` at the bottom: `    Option         "NoFlip" "true"`

### Other generalist behavioral changes to improve performance

1. Open `/etc/modprobe.d/some_file_name.conf`
1. Add this line: `options nvidia_drm modeset=1 fbdev=0`
1. Optionally also add: `options nvidia NVreg_PreserveVideoMemoryAllocations=1 NVreg_TemporaryFilePath=/var/tmp`
1. enable these nvidia unit files
  - nvidia-hibernate
  - nvidia-suspend
  - nvidia-resume

## Todo's

- Figure out how to disable cursor click in term
- Figure out how to get KDE to always launch, optional but would be nice eventually
