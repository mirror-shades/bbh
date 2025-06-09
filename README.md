# Barebones Hyprland

This is a lightweight set up for Arch Linux using hyprland. The footprint is much smaller than the desktop profile via archinstall. You can customize it from there or set up your config file to allow pulling updates from github.

## Initial Setup

1. run the bbh config found here
   - `archinstall --config-url https://raw.githubusercontent.com/mirror-shades/bbh/main/config.json`
2. choose your partition layout
3. make a sudo user profile

## Post-Install Setup

Best to restart and log in rather than chroot after install, but it can be done. the commands might need to be adjusted if doing in root.

### Networking

Connect to WiFi (if needed):

```bash
nmcli dev wifi list
nmcli dev wifi connect <SSID> password <password>
```

### Theme Installation

```
git clone https://github.com/mirror-shades/arch-config.git
sudo cp -r ./arch-config/* ~/.config
```

This allows you to `git pull` in your config folder to update it

```
// managed config
sudo cp -r ./arch-config/.git ~/.config
sudo chown -R $USER:$USER .git
```

You can safely remove the repo now

```
// cleanup
rm -r arch-config
```

### Display Manager

Enable ly display manager. This command only needs to be run once:

```bash
sudo systemctl enable ly
```

### Reboot

```
reboot
```

## Finished

You now have an extremely lightweight rice of hyperland to do whatever you want with. I recommend starting by opening the hyprland config file at `~/.config/hypr` and setting key bindings the way you prefer.

### Programs

- Ghostty (terminal)
- Helix (editor)
- Rofi (programs menu)

### Keybindings

`Super + n` new terminal

- q quit window
- space see programs menu
- [number] switch workspace
- shift + [number] switch window to workspace

You can see and edit keybinding in the hyprland config file.

## Additional steps

Some additional software which may be useful (this will be automated in the future)

### Yay

```bash
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```

### Internet

```bash
yay -S zen-browser-bin
```

### File Explorer

```bash
yay -S yazi
```
