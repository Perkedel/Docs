# macOS DMG Opener For Linux

So, let's say you moved out of macOS and go to Linux. And you still had these `.dmg` files lying around. You're curious how to reextract them again.

Don't worry, at least we got https://github.com/darlinghq/darling-dmg .

## What is DMG file?

it's Apple's way of packing Macintosh softwares. Authors these days distributed them this way.

`.dmg` files are basically a `.vhd` file, believe it or not (no trademark). It's often structured like you would building hard disk image. Or more like, Digital CD. You just mount that up, drag the program to your Program folder, or with an installer included, and unmount it. Tada, installed!

In a rare case, some assets are packed into a harddisk file like this, e.g., because they got weird characters in filename that could damage other file system if it's there, such as NTFS. A filename that's fine in Apple HFS, often time illegal in NTFS, and maybe others.

## How to Darling?

Simple, Just do the command, with argument of what disk file, and where to mount to, followed with familiar FUSE arguments. e.g.

```console
$ mkdir -p ~/.local/mnt/myFuseDmgApp  # Build the mount directory first!
$ darling-dmg cool-mac-app.dmg ~/.local/mnt/myFuseDmgApp  # then mount that Digital CD!
```

It uses FUSE to do this. Darling will choose the first usable data partition in the `.dmg`, and mount that, to path you selected.  
It supports HFS & HFS+/HFSX. Read Only access to this day.

Unmounting is easy as well! Just like FUSE typically,

```console
$ umount ~/.local/mnt/myFuseDmgApp
```

> [!TIP]  
> It is recommended to mount in user-accessible directory like `~/.local/mnt`, instead of root-only paths like `/mnt`.  
> Dolphin e.g., Root access mode are timed and has expiry in certain minutes after a while. Additionally, it is highly discouraged to run file manager in root mode just to get it done.

## Illegal Filename

If a file had illegal filename in the target filesystem, your file manager should offer you to filter-rename every file found. Such as Dolphin. All illegal characters will automatically turn into `_`.

## 7z

Unfortunately, many distro & user repository that shipped 7z has a rather gacha reliability. Some files work, some files do not. The Darling CMD alas, is your only option.

## Windows?

https://superuser.com/a/321169/1036816 . Sorry, I can't find the concrete info about it.

## Convert to ISO?

https://osxdaily.com/2009/09/09/convert-a-dmg-to-iso-and-convert-iso-to-dmg-on-mac/

I hope you still have macOS left, because you can use the same `hdiutil` to convert those `.dmg` file into ISO, such as:

```
hdiutil convert /path/imagefile.dmg -format UDTO -o /path/convertedimage.iso
```

Now you can use any ISO compatible software to extract it yey.

btw, to convert it back

```
hdiutil convert /path/imagefile.iso -format UDRW -o /path/convertedimage.dmg
```

## Wrapper

Unfortunately, I was unable to find AUR of https://github.com/go-darwin/hdiutil .