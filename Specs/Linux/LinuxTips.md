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

- CachyOS .......
- Arch Wiki here random pls