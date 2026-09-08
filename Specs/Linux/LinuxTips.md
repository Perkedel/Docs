# Kaorfa's personal Linux Tips

Here are random tips of Linux & maybe other Unix-like based OSes

## Command Line

### Arch Linux Package Managements, btw

Assuming you got extended ALPM command app such as

- `paru`
- `yay`
- `pacaur`
- etc.

here are reminders how to update package on your Arch installation, btw. change `paru` into whatever ALPM helper you used

#### Install something

```sh
paru -Sy package_here another_one and_another ...
```
Refresh database (`-y`) and install `package_here`, `another_one`, `and_another`, and so on separated by space.

#### Update all

```sh
paru -Syu
```
To refresh database (`-y`) & install all updates (`-u`)

#### Uninstall

```sh
paru -R your_package_removing_here and_another and_then_another ...
```
to uninstall package. Removes the `your_package_removing_here`, `and_another`, `and_then_another`, and so on separated by space.

#### "Key Invalid" Errors

Pacman key suddenly goes invalid? Try one or some of these

- `sudo pacman-key --refresh-keys` to refresh all of your keyring.
- Reinstall / Update Keyrings too
  - `sudo pacman -Sy archlinux-keyring` reinstall or update built-in Arch Linux keyring.
  - `sudo pacman -Sy cachyos-keyring` and CachyOS keyring too.
  - `sudo pacman -Sy gnome-keyring` (OPTIONAL) also the GNOME's keyring for good measure
  - (OPTIONAL) & `debian-*-keyring` too?
  - whatever
- extra sauce
  - https://bbs.archlinux.org/viewtopic.php?id=289895
  - https://gitlab.archlinux.org/archlinux/archlinux-keyring/-/work_items/187
  - the `archlinux-keyring-wkd-sync`???

#### Emergency Pacman

Let's face it. Your SSD even the ones designed for Datacenter won't last long and none are perfect.  
And additionally, you still had no UPS somehow, either it's just too expensive, or it pumps bills way too high.  
And so, while you update, out of all time power fails & the PC lost power, which corrupted essential stuffs in it, including your `pacman`.  
A good practice that you should've always done if you haven't already, is to always prepare a static backup variant of `pacman` so you can fix it up.

Install `pacman-static` from AUR

```sh
paru -Sy pacman-static
```

This package is source code, so it has to compile for very long time, because since it's static, it inserts all those dependencies and libraries directly into 1 single binary file.
Alternatively, you can download precompiled binary version somewhere, or even from some of the Arch ISOs, who knows.  
Once you have `pacman-static` you can use it on even said severely corrupted system.

Then you can run `pacman-static -Syu` e.g. (or whereever `pacman-static` located at), to reupdate all and hopefully fix something that was broken.

#### Offline Pacman

Make your Arch Linux prep all upgrades now & install them after shutting down / restarting, just like Windows. We'll use [Cachy's extended help](https://wiki.cachyos.org/configuration/post_install_setup/#updating-the-system). But also here [source code](https://github.com/eworm-de/pacman-offline).

- Install `pacman-offline`! `paru -Sy pacman-offline`
- Edit the pacman config! `/etc/pacman.conf`
  - add line `Include = /etc/pacman.d/offline.conf` around other includes somewhere. And this `offline.conf` file contains ignore (`IgnorePkg` setting lines) setting during manual `paru -Syu` upgrades. 
- create new file `/etc/pacman.d/offline.conf` & fill with those ignore lines. **[See the guide](https://wiki.cachyos.org/configuration/post_install_setup/#updating-the-system)**. You have to use CachyOS's extended ignore lines, especially if you're using CachyOS & derivatives.
  - Yes, basically it's ignore all kernels both OG & derivatives when manually updating, & only do so for offline prep.
- Then start the preparer once now! `sudo systemctl start pacman-offline-prepare.service`
- It is also advised to enable its included systemd task scheduler `sudo systemctl enable pacman-offline-prepare.timer` so it'll start preparing minutes right after you booted in on a daily basis.
- Reboot now!
  - If you got a package prepared to the pending, the `pacman-offline` will begin installation first right around before halt. **Please do not panic if your shutdown plymouth goes blank for a very long time**, This should be normal & your updater is installing those upgrades. **Then the updater continue the shutdown / restart** afterward. Your Plymouth or your graphic driver might have bug, but otherwise is nonlethal.
- Enjoy your shutdown updater ala Windows! You can now lean lazy where atleast all of your kernels always be ready for every upgrade.
  - **TIPS!** **It is highly advised to leave rest of the noncritical updates to just notification** rather than install right away (just like Windows & other apps on the OS doing). [Forum](https://bbs.archlinux.org/viewtopic.php?id=247428), [Reddit](https://www.reddit.com/r/archlinux/s/K1WpNH4rb2), [Stack Exchange](https://unix.stackexchange.com/questions/139065/how-can-i-responsibly-run-updates-automatically-on-arch-linux).
- You can also enable annoying auto-reboot too just like early Windows 10 days, `sudo systemctl enable pacman-offline-reboot.timer`, essential for Server tho. By default, this service file define auto-reboot by every 3 AM of your timezone (with randomized delay by 2 hours around) whenever `pacman-offline` found prepared upgrades pending.

#### Recommended Shelly Configs

> **😍 TOWEWEWEWEW!!!**

Checkout file `~/.config/shelly/config.json` for your Shelly CLI configurations. example how it should look like,

```json
{
  "FileSizeDisplay": "Megabytes",
  "ParallelDownloadCount": 10,
  "DownloadAddressFamilyPolicy": "PreferIPv4",
  "ProgressBarStyle": "Blocks",
  "ProgressBarWidth": 24,
  "OutputMode": "singlepane",
  "AppImageInstallPath": null,
  "AutoConfirmCacheClean": false,
  "AurUrl": "https://aur.archlinux.org"
}
```

> [!TIP]  
> You can also use `shelly config set YourConfigHere value` to set it right away.

And we recommend that you change

- `AutoConfirmCacheClean` to **`true`**. Auto click yes clean caches when you update-upgrade system.
- `DownloadAddressFamilyPolicy` to `PreferIPv6`. Connects update source through IPv6 first & foremost, and fall back to IPv4 if your network somehow failed to have one. Looking at you, Southeast Asian internet except Singaporeans & International policy powered ISP (such as [CBN](https://cbn.id/) here on many Indonesian office buildings and appartments)

For GUI version, see GUI Settings.json section

### Too Long Didn't Read

```sh
tldr your_command_line_here
```

quick help for your command line stuffs, if `man your_command_line_here` is way too complicated.

Update TL;DR with

```sh
tldr --update
```

### Fastfetch

Show off cool system info now! You can get `fastfetch` right from your Arch distribution & its derivatives.

```sh
paru -Sy fastfetch
```

and run it

```sh
fastfetch
```

btw, CachyOS already has one and in-fact `rc`ed it for everytime you started a terminal session. You can see that it is a distro preconfigured effect on your `fish` sh configuration, system-wide

> [!CAUTION]  
> You do not need to add this `fish_greeting` function again in this `/usr/share/cachyos-fish-config/cachyos-config.fish` file below.

```
 /usr/share/cachyos-fish-config/cachyos-config.fish
```

```fish
...
## Set values
## Run fastfetch as welcome message
function fish_greeting
    fastfetch
end
...
```

See the [Source code of fastfetch](https://github.com/fastfetch-cli/fastfetch), [samples](https://github.com/fastfetch-cli/fastfetch/tree/dev/presets/examples), & [Wiki](https://github.com/fastfetch-cli/fastfetch/wiki/Configuration) for more details & tips

### Secure Boot

UEFI Secure Boot is haaaaard, but once you conquered, it feels like you're level 90 MAX with all sub-upgrades facing the same lvl 90 monsters

See [CachyOS's how](https://wiki.cachyos.org/configuration/secure_boot_setup/).

- Install Secure Boot. Assuming you're using GRUB...
  - Prepare GRUB to your ESP with Secure Boot compatibility: `sudo grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=cachyos --modules="tpm" --disable-shim-lock`
  - Go to Motherboard BIOS setting with `systemctl reboot --firmware-setup` or when manually rebooted (to the part when all your USB devices data turned OFF), rapidly tap your BIOS key, either
    - `Del`. **Most motherboards, Recommended**
    - `F2`.
    - `ESC`. If your keyboard is amputation model, i.e. not full 128 keys. 
      - btw, stop adoring those kinds of keyboards for sake of Mechanical Keyboard hasted larping, use 128-key like PC has been since long, such as ones from Keychron, which also has sophisticated mechanical keyboard moodel. E.g., **Keychron K10** highest end & latest revision and forward. This thing is based on QMK (an pen Source Keyboard framework)
  - Backup all Secure Boot keys, put backups to safe places, **and purge all current keys**. Chances are, your Secure Boot variables are messed up due to improper enrollment or whatever complexity attempt you did, or your OS. This will cause unexpected Secure Boot Violation if you're trying to Dual Boot away from Windows. **Just delete all the keys and start over**.
    - Once you deleted all the keys (including `PK` (Platform Keys)), your SB should be automatically fall into `Setup Mode` (because `PK` key is gone as well).
  - Boot back to your OS now!
  - Check once more for Secure Boot status `sudo sbctl status`. Make sure you are indeed in `Setup Mode`
  - Create machine owner keys now `sudo sbctl create-keys`
  - Enroll now with Microsoft! `sudo sbctl enroll-keys --microsoft --firmware-builtin`. **Pay attention 1st to the following motherboard brands bellow whether you should include vendor keys (`--firmware-builtin`) or never**.
    - Must keep adding `--firmware-builtin`
      - Framework
      - Van Elektronische, Murah Series
      - All other brands
    - **Never add `--firmware-builtin`**. Can cause duplicate keys, e.g.
      - ASUS, ROG
      - Gigabyte, AORUS
  - Immediately sign all your boot files you use, with 
    - `sudo sbctl-batch-sign` to sign all used EFI files
    - `sudo sbctl sign /boot/efi/EFI/cachyos/grubx64.efi` to sign that EFI and add it to batch signer.
    - Hardware Firmware updaters (the `fwupd`) too! `sudo sbctl sign -s -o /usr/lib/fwupd/efi/fwupdx64.efi.signed /usr/lib/fwupd/efi/fwupdx64.efi`
      - Don't forget to configure `/etc/fwupd/fwupd.conf`, to have `[uefi_capsule]` with `DisableShimForSecureBoot=true` beneath
    - Sign other EFI files you multi-boot to e.g. `sudo sbctl sign /boot/efi/EFI/idkLinux/grubx64.efi`, and then another, etc.
  - Now check the result `sudo sbctl status` & `sudo bootctl`
    - `Setup Mode` should rise back to `Disabled` because you've enrolled, and that includes the `PK`.
    - If `Setup Mode` still says enabled, try to reboot your system. 
      - Please do not forget to sign your main OS Boot EFI first, 
      - otherwise **temporarily disable secure boot** in BIOS first, 
      - boot back in, 
      - sign it,
      - go back to BIOS & **turn secure boot back on**
      - Boot back in again,
      - bruh.
  - Extra misleading breakers
    - ASUS
      - Secure Boot mode name is ambiguous!
        - `Other OS` = Disable Secure Boot
        - `Windows` = Enable Secure Boot, **You must set it to this** even you're here on Linux.
  - Enjoy secure boot. That was hard, I know!
    - Our Soul Selector supposedly only do checksum, I think.
- Reinstall Secureboot. If you've booted back to Windows (`bootmgrfw.efi`) since 11 and up, it'll mess your BIOS boot order. And finding the GUID of your disk or wherever your OS' GRUB is not easy.
  - Reinstall GRUB again `sudo grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=cachyos --modules="tpm" --disable-shim-lock`. This should once again re-add this GRUB to BIOS & reorder it to boot first
  - Sign the GRUB EFI all over again `sudo sbctl-batch-sign` & `sudo sbctl sign /boot/efi/EFI/cachyos/grubx64.efi`
  - Reboot & Check again `sudo sbctl status` & `sudo bootctl`

### Freedesktop Noisy Sounds

Linux itself too can be as noisy as Windows, as long as the Distro opens this flexibility up.

#### KDE Noisy

Go to KDE Setting, category `Notification`. Here on top left, you can adjust how noisy your KDE Plasma, for system (`Configure for System...`), & apps (`Configure for Applications...`)

- Each event lets you adjust if an event will pop a notify and/or play a sound
- You can set the sound it play with a Freedesktop keyword, or a custom filepath.

#### Canberra

[Canberra](https://wiki.archlinux.org/title/Libcanberra) is the great example implementation of Freedesktop Noisy. Most of the time, you probably already had `libcanberra` installed at some point when you got few apps along the way.

You can also test your system sound based on your currently set sound theme with `canberra-gtk-play` (should be included with `libcanberra` also).  
e.g., to play the Logged in Sound,

```sh
canberra-gtk-play -i "desktop-login" 
```

You can even add that to your WM startup if you're not on KDE, such as Hyprland, to the `hyprland.start` function.  
E.g., my Cachy edit `.config/hypr/autostart.lua` now looks like

```lua
hl.on("hyprland.start", function ()
    --hl.exec_cmd("mpv --no-config -vo=null --keep-open=no --autoload-files=no " .. SOUND_LOGIN)
    hl.exec_cmd("canberra-gtk-play -i 'desktop-login'")
    hl.exec_cmd("dbus-update-activation-environment --systemd --all")
    hl.exec_cmd("gsettings set org.gnome.desktop.interface gtk-theme \"adw-gtk3\"")
    hl.exec_cmd("gsettings set org.gnome.desktop.interface color-scheme \"prefer-dark\"")
    hl.exec_cmd("noctalia")
--     hl.exec_cmd("caelestia shell -d")
    hl.exec_cmd("xhost +SI:localuser:root")
end)
```

#### Change Sound Theme

There are ways you can change your sound theme afaik

- KDE. Use its System Setting
  - `Color & Themes`, `Global Theme`, `System Sounds`. There you can choose which one. **You can even download some more from provided Community store there**

#### Where to get more sounds?

Well there are ways.

- A `P` *Community Store* like [Gnome Looks](https://gnome-look.org), [KDE Store](https://store.kde.org/), should be same or similar contents under different skin, I suppose.
  - Beware, to not open all of those tabs at once (and/or in an outdated or LTS Chromium like Thorium), otherwise you'll get your public IP wholly gets banned into simply `Forbidden` text next qeury. At this point, **all devices in your WiFi network no longer can access that domain anymore**. You may wanna wait until your ISP reroll your Public IP or ask them new one, or perhaps until the `P` server software relieved your Public IP off of your punishment in time, idk.
- Repositories, usually contains `*sound-theme*` in its name. Look it up!, `paru -Ss sound-theme`.
- Accidental find on GitHub, maybe? But how??
  - In any case, the [`Minimal Sound UI`](https://github.com/cadecomposer/modern-minimal-ui-sounds) from cadecomposer (CC4.0-BY-SA) sounds good to me. Not by GitHub, it's there on `P` store.
    - But alas, while both ingredients & Reaper project included in the source code, somehow the machine and the components have been far upgraded beyond the last commit of the source code. 
    - **Therefore we can no longer reconstruct the signature of these sounds** to make more funny sounds. 
    - [Here's the wonky attempt so far](https://github.com/Perkedel/BringYourOwnUSB-SFW/blob/main/Mods/Soundfont/Vital/LostModernPiano_trymore.vital). It's a Vital's sine, made into Piano, where the Hold was pushed really down, focus just on the Attack & a little bit on Release.
    - Think of it like making a new Piano from Surreal Blender Meme abstract materials. How would it sounds when a felt hammer hits a string.

#### Install the sound theme!!

There are 2 places. Put a folder of a theme into which location you'd like

- 1 User only `~/.local/share/sounds`. That user will be the only one that can see the sound theme. Use only for quick testing and other too-tedious-to-sudo installations.
- System-wide `/usr/share/sounds`. Requires `sudo` but will guarantee reliable working condition down to login managers.
  - Login manager sounds `system-ready` if it does trigger so like [GDM](https://wiki.archlinux.org/title/GDM), remember Ubuntu's `system-ready` African drum jingle?

#### List of Freedesktop Sound Naming

See the [sauce from 0pointers.de yeay](https://0pointer.de/public/sound-naming-spec.html) for mostly up to date namings. Update as of 2026

- Alerts
  - `network-connectivity-lost`. The sound used when network connectivity is lost.
  - `network-connectivity-error`. The sound used when an error occurs when it is tried to initialize the network connection of the computing device.
  - `dialog-error`. The sound used when a dialog is opened to explain an error condition to the user.
  - `battery-low`. The sound used when the battery is low (below 20%, for example).
  - `suspend-error`. The machine failed to suspend.
  - `software-update-urgent`. The sound used when an urgent update is available through the system software update program.
  - `power-unplug-battery-low`. The power cable has been unplugged and the battery level is low
- Notifications
  <!--- ``. -->
  - `message-new-instant`. 
  - `message-new-email`. 
  - `complete-media-burn`. 
  - `complete-media-burn-test`. 
  - `complete-media-rip`. 
  - `complete-media-format`. 
  - `complete-download`. 
  - `complete-copy`. 
  - `complete-scan`. 
  - `phone-incoming-call`. 
  - `phone-outgoing-busy. 
  - `phone-hangup`. 
  - `phone-failure`. 
  - `network-connectivity-established`. 
  - `system-bootup`. 
  - `system-ready`. 
  - `system-shutdown`. 
  - `search-results`. 
  - `search-results-empty`. 
  - `desktop-login`. 
  - `desktop-logout`. 
  - `desktop-screen-lock`. 
  - `service-login`. 
  - `service-logout`. 
  - `battery-caution`. 
  - `battery-full`. 
  - `dialog-warning`. 
  - `dialog-information`. 
  - `dialog-question`. 
  - `software-update-available`. 
  - `device-added`. 
  - `device-added-audio`. 
  - `device-added-media`. 
  - `device-removed`. 
  - `device-removed-media`. 
  - `device-removed-audio`. 
  - `window-new. 
  - `power-plug`. 
  - `power-unplug`. 
  - `suspend-start`. 
  - `suspend-resume`. 
  - `lid-open`. 
  - `lid-close`. 
  - `alarm-clock-elapsed`. 
  - `window-attention-active`. 
  - `window-attention-inactive`. 
- Actions
  - a
- Game
  -  a

For OpenCX Phronted Sound event name, refer to the document, TBA.

> [!NOTE]  
> Teaser!  
> - Notification & Dialog  
> - Sound Alert, PC Beep Alert, LED Alert
> - Haptic Mirror or dedicated audio haptic, Vibration Alert

## Graphical User Interface

### ALPM with GUI will ya?!

#### Updater Too Terminally, yuck!

Use **[Shelly](https://github.com/Seafoam-Labs/Shelly-ALPM)**, **NEW!!!**

Available by default for CachyOS, btw. Install if you hadn't already.

```sh
paru -Sy shelly
```

It should automatically pick from `cachyos` internal repository **which is Recommended**. But if unsure, feel free to just `sudo pacman -Sy shelly` instead, to really-really go to `cachyos` fr.

> [!IMPORTANT]  
> afaik, only CachyOS has `shelly`. Other Arch based distro may not have such and therefore should go to AUR, unfortunately. Simply use above `paru -Sy shelly` for best result and pay attention where did your AUR-ALPM helper go to.

You can now launch Shelly from your Start Menu, find `Shelly`. Or they got cool CLI too!

Upgrade from CLI with

```sh
shelly upgrade all
```

#### Shelly GUI Setting File

> 😳🥵 GYAAAAAAAAAAAAAAT!!!

Checkout file `~/.config/shelly/settings.json` for your Shelly CLI configurations. example how it should look like,

```sh
{
  "Culture": "",
  "NewInstall": true,
  "NoConfirm": false,
  "AurEnabled": false,
  "AurWarningConfirmed": false,
  "AppImageEnabled": false,
  "FlatPackEnabled": false,
  "RecommendedEnabled": true,
  "ShellyIconsEnabled": true,
  "ShellySearchEnabled": false,
  "WebviewEnabled": false,
  "DefaultPageDropDown": "packages",
  "NavMode": "sidebar",
  "WindowLastWidth": 0,
  "WindowLastHeight": 0,
  "PackageInstallView": "grid",
  "PackageManagementCascadeDelete": true,
  "PackageManagementRemoveConfigs": false,
  "PackageManagementRemoveOptionalDeps": true,
  "PackageInstallUpgrade": false,
  "PackageInstallShowHidden": false,
  "PackageInstallShowExplicitOnly": false,
  "PackageInstallShowDependsOnly": false,
  "PackageInstallShowDetailPane": false,
  "AurInstallUseChroot": false,
  "AurInstallRunChecks": false,
  "AurInstallShowDetailPane": false,
  "AurInstallDisableDevel": false,
  "AurRemoveCascadeDelete": true,
  "AurUpdateRunChecks": false,
  "AurUpdateShowHidden": false,
  "SearchShowDetailPane": false,
  "TrayEnabled": false,
  "TrayAutoStart": false,
  "TrayCheckIntervalHours": 72,
  "UseSymbolicTray": true,
  "TrayIconPath": "",
  "TrayUpdatesIconPath": "",
  "UseUiForUpdate": false,
  "UseWeeklySchedule": false,
  "DaysOfWeek": [],
  "Time": ""
}
```

And we recommend that you change

- `ShellySearchEnable` to **`true`**. Enable second search package view. This one works differently, searches packages from all 3 kinds of universe, and lets you easily filter between `Standard`, `AUR`, & `Flatpak` results.

### KDE Configuration Module

You can add more Setting category in your KDE Setting app by installing `*-kcm` packages. e.g.,

- Plymouth (Fedora's Boot Splash) setting with `plymouth-kcm`. Find this in `Color & Themes`, `Global Theme`, `Boot Splash`. Now you can graphically select your favorite boot splash!
- SDDM with `sddm-kcm`. Also can be found in above theme category setting, at `Login Screen (SDDM)`. You can now graphically change wallpaper, change design, and resync your themes into it. 
  - **Also pls make sure SDDM service is enabled & disable the others**
    - `systemctl enable sddm`
    - `systemctl disable otherloginmanagers` etc.
- Plasma Login (`plasma-login-manager`, KDE Plasma dedicated fork of SDDM) already included KCM. Find this in `Login Screen` inside `Security & Privacy` separator. However unlike OG SDDM, **you can only have 1 design**, which is KDE Plasma design. Therefore you can only change Wallpaper & resync your Theme settings to it. 
  - **Also make sure Plasma-login is enabled & disable the others**
    - `systemctl enable plasmalogin`
    - `systemctl disable otherloginmanagers` etc.
- Some packages may include KCM on their own.
- What else?

## Depreacated, ignore!

### Neofetch (DEPRECATED)

~~Show off cool system info now! You can get `neofetch` right from your Arch distribution & its derivatives.~~ Old & no longer maintaied

```sh
paru -Sy neofetch
```

and run it

```sh
neofetch
```

## Sauces I got

Assorted sauce

- [CachyOS](https://wiki.cachyos.org/) .......
- Arch Wiki here random pls
- [Shelly](https://www.seafoam-labs.org/)