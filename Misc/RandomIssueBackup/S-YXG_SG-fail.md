# S-YXG Combination SG fail on Wine

Looks like I still have problem on a sub-worker of this Combination, particularly the SG one.

## Spec

OS = [CachyOS](https://cachyos.org/) rolling (Based on Arch Linux). `amd64`  
WINE = 11.17 Staging. the 64-bit has experimental WoW64 support  
Player = Falcosoft Soundfont MidiPlayer 32-bit

- Falcosoft & Combination folders in the `~/WinApp` directory
- Using special launch arguments, see below steps
- Use WINE Staging (`wine-staging`)! Stable variant (`wine`) won't work at all.

## Steps

- Attempt to replicate above setup. Important to have the Host & Wine 64-bit, which is by already by default.
- Run Falcosoft as normal under wine. The 32-bit variant indeed only has x86 support, therefore it should automatically engage WoW64. 
  - I recommend to use my [Launcher shortcut here](https://github.com/Perkedel/BringYourOwnUSB-SFW/blob/main/Mods/Linux/ShellScripts/MidiPlayer_virtualDesktop.sh). 
  - Just plop this shell script next by `MidiPlayer.exe`
  - Make the script executable `chmod +x MidiPlayer_virtualDesktop.sh`.
  - Then execute `./MidiPlayer_virtualDesktop.sh`
  - It is here because on my KDE Plasma, split-windowed app like this causes positioning trouble and focus steal bugs. What essentially done is that I put the app inside a Wine Explorer virtual desktop, so it tries to contain & emulate Windows' WM fully.
  - Also It's my personal trouble. Wine we got somehow missing Bahasa Indonesia, and my system is in `Indonesian`. Without exporting `LC_ALL` to `en_US.UTF8` (Force Locale to American English for this session), Wine will select fallback language whatever is the first, which usually `Arabic`.
- **Play some SG songs**. Songs in that SG sample sets.
- Observe as whenever it ask e.g. `Female music New` SG voice, **The SG worker somehow failed to run**.
- **This doesn't happen to PV worker**. It runs fine.
- Optionally try again but manually forcing the architecture to `wow64` just for this terminal session.
  - Really make sure you've been doing this whole time on 64-bit prefix, which by the time of installation in your 64-bit Linux, you already did & had one.
  - Before launching the app, add `export WINEARCH=wow64`
  - or manually, before running the script, `export WINEARCH=wow64`
  - Just in case. Again, unnecessary I think, since the 32-bit variant of `MidiPlayer.exe` only had that 32-bit heading and would always cause WoW64 to engage.

## Logs

### SG Crash wine log 2026-09-17, S-YXG2006LE Hybrid

<detail>
    <summary>Here WINE crash dump</summary>
```log
Unhandled exception: page fault on write access to 0x0012115e in wow64 32-bit code (0x201431e9).
Register dump:
    CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:002b
    EIP:201431e9 ESP:0022f888 EBP:0022f888 EFLAGS:00010206(  R- --  I   - -P- )
    EAX:00121144 EBX:00000001 ECX:00116501 EDX:00cea176
    ESI:00000000 EDI:0000ac44
Stack dump:
0x0022f888:  0022f8b0 201533e0 00000000 00000001
0x0022f898:  00000000 00000001 0000ac44 00980020
0x0022f8a8:  201419f8 00000000 0022f8bc 20149146
0x0022f8b8:  00000000 0000ac44 00405f10 00000001
0x0022f8c8:  00980020 0022f91c 1c200800 004060d3
0x0022f8d8:  0000ac44 00a80020 00c8007c 00c8007c
Backtrace:
=>0 0x201431e9 (0x0022f888)
    1 0x201533e0 (0x0022f8b0)
    2 0x20149146 (0x0022f8bc)
    3 0x00405f10 in syxg2026-sg-worker (+0x5f10) (0x0000ac44)
0x201431e9: movb %cl, 0x1a(%eax)
Modules:
Module  Address                 Debug info      Name (5 modules)
PE        400000-  535000       Dwarf-4         syxg2026-sg-worker
PE-Wine 7b0f0000-7b3cb000       Deferred        msvcrt
PE-Wine 7b500000-7ba9e000       Deferred        kernelbase
PE-Wine 7bab0000-7bc2f000       Deferred        kernel32
PE-Wine 7bc70000-7bfe1000       Deferred        ntdll
Threads:
process  tid      prio    name (all IDs are in hex)
00000038 services.exe
0000003c    0     
00000040    0     
0000004c    0     
00000078    0     
0000008c    0     
000000a8    0     
000000e8    0     
00000108    0     
00000114    0     
000001b8    0     
0000080c    0     
00000044 winedevice.exe
00000048    0     
00000054    0     
00000058    0     
0000005c    0     
00000060    0     
00000064    0     
0000009c    0     
00000070 svchost.exe
00000074    0     
0000007c    0     
00000080    0     
00000084 plugplay.exe
00000088    0     
00000090    0     
00000094    0     
00000098    0     
000000c4    0     
000000a0 winedevice.exe
000000a4    0     
000000ac    0     
000000b0    0     
000000b4    0     
000000b8    0     
000000bc    0     
000000c0    0     
000000dc    0     
000000f0    0     
000000f4    0     
000000fc    0     
00000100    0     
000005b0    0     
000005b8    0     
000005bc    0     
000005d8    0     
0000010c rpcss.exe
00000110    0     
00000118    0     
0000011c    0     
00000120    0     
00000124    0     
000007a4    0     
000007fc    0     
00000034    0     
000001ac MicrosoftEdgeUpdate.exe
000001b0    0     
000001bc    0     
000001c0    0     
000001c4    0     
000001c8    0     
00000804 lsass.exe
00000808    0     
00000814    0     
00000818    0     
0000081c    0     
00000724 start.exe
00000730    0     
00000728 explorer.exe
00000718    0     
00000720    0     
00000768    0     
0000077c    0     
000007b4    0     
00000778 MidiPlayer.exe
00000784    0     
000007d4    0     
000007ac   15     
000007b8    0     
000007bc   15     
000007c0    2     
000007c4   15     
000007c8    0     
000007cc    0     
000007d8    0     
000007dc    2     
000007e0   15     
000007e8 (D) Z:\home\joelwindows7\WinApp\Andre_Louis\S-YXG2026 Hybrid\VST\syxg2026-sg-worker.exe
000007ec    0 <== 
00000028    0     
000007f0 conhost.exe
000007f4    0     
00000190 explorer.exe
000000ec    0     
000000e4    0     
00000798    0     
000007a0    0     
System information:
    Wine build: wine-11.17 (Staging)
    Platform: x86_64 (guest: i386)
    Version: Windows 10
    Host system: Linux
    Host version: 7.2.4-1-cachyos

```
</detail>

<detail>
  <summary>On Terminal</summary>
```log
...
014c:fixme:explorerframe:taskbar_list_ThumbBarUpdateButtons iface 00A414A8, hwnd 000F002C, cButtons 1, pButton 00EB19FC stub, faking success!
014c:fixme:explorerframe:taskbar_list_SetProgressState iface 00A414A8, hwnd 000F002C, flags 2 stub!
014c:fixme:explorerframe:taskbar_list_SetOverlayIcon iface 00A414A8, hwnd 000F002C, hIcon 002001E8, pszDescription L"Playing" stub!
014c:fixme:explorerframe:taskbar_list_SetProgressValue iface 00A414A8, hwnd 000F002C, ullCompleted 36, ullTotal 1758f stub!
wine: Unhandled page fault on write access to 001214A6 at address 201431E9 (thread 0780), starting debugger...
073c:fixme:dbghelp_dwarf:compute_location Unhandled attr op: 9c
073c:fixme:dbghelp_dwarf:compute_location Unhandled attr op: 9c
073c:fixme:dbghelp_dwarf:compute_location Unhandled attr op: 9c
...
```
  
</detail>

## Extras

### Related issues

- https://github.com/OnjLouis/syxg100-hybrid/issues/4