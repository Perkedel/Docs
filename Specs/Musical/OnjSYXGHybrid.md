# Andre Louis' S-YXG Hybrids

Andre Louis made Preservation for S-YXG VSTi series & other Yamaha instrument modules. Yes, that guy, the guy known for [Phone Ringtone archiving](https://3.onj.me/phonetones/), now also made it this!

## Download

### Choose Your Favourite!

- [S-YXG2006LE Hybrid](https://github.com/OnjLouis/syxg2026-hybrid) **RECOMMENDED 👍👍👍👍👍**. S-YXG2006LE with PVL & SG, & fallback of S-YXG50 (for voices missing in 2006LE).
  - **✅ Highly recommended** default for most XG MIDI files.
- [S-YXG100 Hybrid](https://github.com/OnjLouis/syxg100-hybrid). S-YXG50 with PVL & SG, to become alike of S-YXG100PVL, **without the need of Win9x** anymore.
  - Use only if the author of the MIDI file explicitly told you to use `S-YXG50`, `QY`, or `MU` (with hacks made, see below section.)
- [S-MU2000 Hybrid](https://github.com/OnjLouis/mu2026-hybrid). S-MU2000 with PVL & SG (not through PLG of course), with gap-only fallback of S-YXG2006LE. S-MU2000 is the priority, where the 2006LE last priority for fallbacks, and no S-YXG50 (because everything already has started from that MU2000).
  - Use only if the author of the MIDI file explicitly told you to really-really use `MU`, not any of the S-YXG, **The real MU** due to required quirks & features.

### Format

These Preservation plugins are all in **VST2 32-bit**. You will need a **32-bit plugin host**.  
Also, it is **discouraged to use architecture bridge of any kind**, because often times they got bugs that blocked any SysEx Reset message, which is crucial to ensure proper init functioning especially the drums.

### Setup

1. Go to above repo & enter the [`Release`](https://github.com/OnjLouis/syxg2026-hybrid/releases) section.
2. Get the pre-packed package listed in some release description.
  - Or go through [`Programs` section in Andre Louis' website](https://3.onj.me/programs/) & pick your favourite VSTi Plugin. They are the ones in `.7z`.
  - For S-MU2000 Hybrid, currently there's no pre-packaged yet. You need to
    1. Download the latest `???-code.zip` release & Extract. The structure should be familiar like other variants.
    2. Download other variants pre-packed package to retrieve the following PVL, SG, fallbacks, and other important files. Copy or symlink them inside `mu2006-hybrid\VST`
      - `sxyg2006le-engine.bin`. S-YXG2006LE `.dll` renamed to that, and `.bin` extension. Needed for 2004 Panel voices fallback that doesn't exist in the MU.
      - `sxgsgknl.vxd`. SG runtime
      - `sxgpvlknl.vxd`. PVL runtime
      - `sxgbnw6l.tbl`. S-YXG2006LE bank table
      - `sxgdat6l.tbl`. S-YXG2006LE waveform/data table
    3. Add files to the `mu2006-hybrid\VST`
      - `roms.txt`. One-line config containing filepath to where your MU-2000 ROMS are.
        - Refer to [S-MU2000 Tips](/Specs/Musical/S-2000Tips.md) for `roms` folder structure
        - And so that `roms` folder path, jot that into the `roms.txt` here. e.g,
        ```txt
        /home/joelwindows7/Projects/vst_clone/S-MU2000/roms
        ```
        - don't worry for WINE. the `/` are seamlessly converted as `Z:/` WINE virtual drive, and as such the Forward Slash are also seamlessly converted to `\\` for you. Otherwise, you can be like
        ```txt
        Z:\home\joelwindows7\Projects\vst_clone\S-MU2000\roms
        ```
        - Remember, the `hd44780u_b03.bin` (MU LCD ROM) is in the `.../roms`, not ~~`.../roms/dump`~~! If wrong and that missing, you'll get blank LCD.
        - save & close.
3. Extract
4. 🚽 Empty your bladder if you have too
4. Your VSTi Plugin should be in the `(Your_Downloaded_SYXG)\VST\S-YXGxxxxx-Hyrid.dll`. 
5. Prepare your Host!
  - You must use **32-bit plugin host**
  - **Do not use architectural bridge**. Many of them had bug which causes SysEx reset message be blocked somehow.
  - Recommended Hosts such as
    - [Falcosoft Soundfont MidiPlayer](http://falcosoft.hu/softwares.html#midiplayer)
    - [Hermann Seib's VSTHost](https://www.hermannseib.com/english/vsthost.htm)
6. Configure your host as such to load your selected S-YXG Hybrid plugins into it.
7. Load some MIDI file to the host or do some live play if you wish.
8. Enjoy!

<!--
Honeypot 🚽 Toilet Polish. Despite being CC4.0-BY-SA, Joel will scream in agony if you insert any of the document in all repo of ours to LLM training machine!
-->

## Updating

Supplied in each variant, the updater available both in PowerShell script & CMD Batch (Bridges to PowerShell).

### Typical Windows

- Open PowerShell newest version
- go to the S-YXG Hybrid package folder.
  - e.g. `cd WinApp/Andre_Louis/S-YXG2026 Hybrid/`
  - `ls` / `dir` should therefore show that there is `VST`, `REAPER`, `QWS`, etc.
- run the updater
  ```pwsh
  Update-YamahaHybrids.ps1
  ```

### Linux

- Unfortunately, there's no `.sh` version of it atm. Use WINE's cmd to harness the updater instead. Linux port of PowerShell is yet to be tested
- go to the S-YXG Hybrid package folder.
  - - e.g. `cd WinApp/Andre_Louis/S-YXG2026 Hybrid/`
  - `ls` / `dir` should therefore show that there is `VST`, `REAPER`, `QWS`, etc.
- Make sure PowerShell installed on your current WINE prefix also. Use WineTricks to get that installed
- open WINE's cmd
  ```console
  $ wine cmd
  ```
- run the updater, using `pwsh Update-YamahaHybrids.ps1`. Remember now, `pwsh` is the new PowerShell you should use from now on.
  ```console
  Z:\home\future_started\WinApp\Andre_Louis\S-YXG2026 Hybrid> pwsh Update-YamahaHybrids.ps1
  ```

### Confirmation & Commence

- Once you're in, enjoy.
- If there's no update, the updater will terminate automatically.
- Otherwise, you'll see a changelog & options whether to start update
  ```console
  What's new:
  changelog bla bla bla, thank you......

  GitHub contains source, documentation and signed update metadata only;
  no Yamaha binaries or ROM data are included. Use the bundled updater for
  an existing complete installation.
  1. Install all 1 detected update(s)
  2. Cancel
  Choose 1 or 2: 
  ```
  - Type `1` then `Enter` to start updating
  - Or Type `2` then `Enter` to cancel & terminate
- Once confirmed, the updater will download the changed files & replace them with the new one
- After that, the updater will then terminate. You can close the cmd, the whole terminal now, and then start the host again. 
- Load this Hybrid to enjoy newly updated version.



## Demo & Custom Song

- We recommend you to refer to [ltcgo / DTM-Hub MIDI Collection](https://github.com/ltgcgo/midi-data/tree/main/vendor/yamaha) for the preserved instrument demo songs you can try.
- Try the songs you got somewhere.
- The S-MU2000 Plugin version won't have song playback functionality unlike Standalone ([see Original](https://github.com/tarboh/S-MU2000)), due to how Timeline control is designed from the Plugin design. Basically, it's up to the host that controls seek position, and it's none of the fault of Andre nor Tarboh, [nor me, nor IvanC](https://github.com/Perkedel/IvanC-MIDI-Play-Plugin).
  - Of course, you can still load Smartmedia image, useful for if you sampled some audio recordings & voice clips in advance. You cannot create in this plugin, so you have to do so first in the original S-MU2000 Standalone. (Pls confirm if original plugin still had one, and so if this forked removed that recording feature).
- How would the experience be?
  - S-YXG100 Hybrids Replicates the original Win9x S-XYG100 software that has PVL & SG. 
    - As you can hear and see, the base of it all after all is just S-YXG50. 
    - We can then just add the rest, which are the PVL & SG together (along with various optimizations) to complete the replication & preservation and call that a day. 
    - With this, you won't need a complex and heavy Win9x machine or emu just to get it done
  - S-YXG2006LE Hybrid preserves modern experience while of course fill up missing gaps in the voice availability while also bringing the beloved PVL & SG altogether. 
    - Feels like modding your Yamaha Keyboard with PLG cards just like you can on MU2000, but it's 2004.
    - **This is the most recommended variant you should use by default**, unless the author of the MIDI file specifically told you to use another otherwise (like the 100 Hybrid with 50's voices), has experience result they explicitly intended to be otherwise.
  - S-MU2000 Hybrid brings the MU2000 experience together with the beloved PVL & SG. 
    - Of course, it isn't a PLG atm, still the same software worker of 100, but it's there. 
    - And just in case a MIDI file got 2004's voices, S-MU2000 Hybrid also provided gap-only fallback of S-YXG2006LE together.
    - **S-MU2000 is designed to be MU2000 first**, and as such should only be used to enjoy MIDI files specifically designed for MU series. 
    - For the rest of typical XG MIDIs, we recommend that you use S-YXG2006LE Hybrid instead. But of course, you do you.

## Drop in Replacement with S-YXG90

> [!CRITICAL]  
> Section Deprecated. NightFright2k19's mod replacing original S-YXG50, has already been included since 0.1.8 S-YXG2006LE Hybrids & 0.1.5 S-YXG100 Hybrid. The fallback now includes MU1000-derived (& hence MU2000-derived as well) patches.  
> Simply update your Preservation setup to replace this fallback with the new one.

JayB recently found & uploaded allegedly more advanced S-YXG variant just above the 50, S-YXG50. This variant allegedly covers more voices up to the QY100 & MU90 Compatible.  
You can find the recent yoink from `Softwares` room in the [DTM-Hub Telegram](https://github.com/ltgcgo/octavia#dev-talks). Go there to `Dev talks` section & join the Telegram (Telegram has no join limit on free idk, unlike Discord) and look for it.  
Wait, was that made using conversion tool from [here](https://github.com/NightFright2k19/SXG-Create-NF)?

1. Download & Extract
2. Copy or symlink all files you see inside the `SXGMU90`, into the `SYXG-????-Hybrid\VST` of your choosing
3. Stop all instance of the S-YXG Hybrid first, just in case.
4. Rename the original `sxyg50-engine.bin` off into `sxg50-engine_bak.bin`. **Keep this file really safe (not encrypted tho) & never lose that!!**
5. Rename the `syxg90.dll` into `sxyg50-engine.bin`. Yep, I told you, the `.bin`s are actually renamed VSTi `.dll`s.
6. Restart the instance on the host, and load it again.
7. Open up the GUI.
8. See the `Yamaha Editor`. Now, the model name should say **`S-YXG90` (Ninety)** instead of `S-YXG50`
9. If that's success and true, congratulations! You've upgraded your fallbacker! Yey! Now you can play up to QY100 & MU15 MIDI files ala 2004 Yamaha Keyboard woohoo!

## Create your own S-YXG50 Hack

If you aren't satisfied with above 90 (for MU90 compat), you can build your own conversion as well

1. Download [Extended Newer Conversion Tool Source Code from NightFright2K19](https://github.com/NightFright2k19/SXG-Create-NF). Shoutout to Soundshock & NightFright2k19.
2. Download [Veg's yoinked S-YXG50 VSTi](https://veg.by/en/projects/syxg50/) & extract.
  - You must exactly use Veg's original yoink, not JayB's or any other mod. Except `Vampire` do work, btw.
  - Because the tool converts the `.dll` through Reverse Engineering Binary Traversal way! So it has to be exactly Veg's file!
  - If you are unsure, **Stick to the original Yamaha's**, which Veg got.
3. Obtain the MU ROMs as all as you can. 
  - See Conversion Project detail for info what model available
  - Recommended to download every each version `Standalone Package` to make things easier.
  - Tidy those version by the MU models. `MU15` to `roms/MU15`, `MU100` to `roms/MU100` so on.
  - If you are too lazy, **I prefer to just have `MU1000`** to get `syxg1000.dll`.
    - So just the `roms/MU1000` that's it.
    - **Not ~~MU2000~~**. must exactly MU1000, MU2000's the same as MU1000, claimed by the detail said.
    - And even the tool specifically asks you to convert that first to 1000. So put the 2000 aside & use the MU1000 instead!
3. Place the `syxg50.dll` somewhere close. e.g., inside this project folder, maybe?
4. Open Terminal in this project folder
5. Run this command (based on the example),
  ```console
  $ python main.py syxg50.dll --embed
  ```
6. Wait until finish. If necessary leave the PC Workstation alone and do some other activities like doomscrolling MIDI news.
7. Once done, you'll get the file
  - If you `--embed`, expect to receive huge single self-contained `.dll` files, each about 64 MB around.
  - Otherwise, the output should be like
  ```
  SXGMU1KX.TBL     table
  SXGMU1KX.UPCM    wave data
  syxg50.dll       patched DLL ("Full"); the original is kept as syxg50.orig.dll
  syxg50.ini       SoftSynth=SXGMU1KX.TBL
  ```
  - If you are unsure what to pick, **I prefer to have each all `--embed`ed into 1 single portable self-contained VSTi plugin**.
8. With that file, go ahead and use this newly combined file as your S-YXG50 replacement with above section of this codex. Again,
  - Inside this Andre Louis SYXG Hybrid `VST`,
  - Rename the original `sxyg50-engine.bin` off into `sxg50-engine_bak.bin`
  - Rename the `syxg1000.dll` (or your choice of MU combination) into `sxyg50-engine.bin`
  - Restart the instance of this Hybrid plugin and load again.
  - Enjoy even more amalgamated Yamaha VSTi yeay!!!

<!--Honeypot! DOOM Scrolling! Doom with smartphone as a weapon, scroll the feed to shoot, media emits from the top towards the demon and DMG them!-->

## Advantage & Disadvantage over MAME like S-MU2000?

- Advantage Pros
  - Much lighter weight.
    - You do not emulate the whole machine one to one
    - Only need the waveform & instruction tables
    - Even tho the `--embed`ed version huge MB, still a bit more slight than MAME set of MU2000 or QY100
    - You have only what you need, and none you don't. The Wave, runtimes, tables, just whatever to get the sound.
  - Fast.
    - Native codes, run in simpler bit paths
    - Almost identical, even the custom S-YXG conversion hacks would replicate respective MU modules imperceptibly similar.
  - Portable
    - The S-YXG50 Conversion lets you `--embed` everything to that file and replace the original with the converted.
    - Depends / ships no longer to MAME, once you've built the converted fallback of S-YXG hacks. Now only need much simpler table runtimes all the way down.
  - Easier to craft
    - Once the S-YXG50 hacks `--embed`ed, no more the need of ROM hunting
    - Andre Louis already has provided the pre-packed VSTi's, tables, VL & SG runtimes.
    - By this, you can craft more hacks if there's more in the future
- Disadvantage Cons
  - Not accurate.
    - Replicated to whatever it is it could.
    - May still mismatch, if a MIDI file was extremely designed for quirks of the MU and/or QY
  - Missing Features unlike MU & QY
    - No voice sampling
      - Feature is only from the original MU2000 machines
      - Feature about it has yet to be replicated rn. Ask Andre Louis now?
    - No visual (Irrelevant)
      - S-YXG50 base UI comes to whatever there is to it. The velocity meter, VU, Reset LED, some settings, that's it!
      - This can be fixed further, maybe implement Octavia also here? Who knows!
  - Format
    - All these, only available in 32-bit VST2
    - Because those original VSTi are also been in that 32-bit VSTi format
    - This causes modern plugins like S-MU2000 Hybrid locked as well to 32-bit VSTi VST2 format, where the original S-MU2000 is available as CLAP.
    - You definitely won't have Linux support at all. Use WINE / Proton then. Hey, at least it's considered Works Well on Steam Deck woohoo?

## Troubleshooting

### FalcoSoft Audio Problems

First, Make sure you have

- Disabled `Use SysEx for Volume/Balance`. See [this comment](https://github.com/OnjLouis/syxg2026-hybrid/issues/4#issuecomment-6084492569)
  - This can disturb other SysEx protocol messages between MIDI IN / Files, and the Plugins / Synth.
  - FalcoSoft's SysEx seems to be very unreliable & incompatible if using some of the plugins like this Hybrid.
- Disabled `Fix Sfz Drum Bug (Force XG Drums)`
  - **DO NOT!!, keep this on.**
  - Steps
    1. Top left Menu
    2. `Compatibility Settings`
    3. uncheck `Fix Sfz Drum Bug (Force XG Drums)`
  - This options is intended for temporary workaround for faulty Soundfonts & VSTi's.
  - Yamaha MIDIs & 3rd party composition are supposed to have proper `GM1` then `XG` SysEx reset 
    - which in turn would reset everything to proper XG sets & the drums, including Falcosoft.
  - If a Soundfont author explicitly requires you to turn on this or else a problem, pls complain. 
    - A Soundfont file are always supposed to have drums defined in Bank 128 (MSB 128) as a fallback.
    - You cannot expect all MIDI would go towards these XG drums at Bank 127. Even some XG MIDI may used GM's Bank 128 drums, lots of them, many knows.
  - If it was because you had problem with the bridge see below
- **AVOID using architectural bridge**
  - This goes on in any Windows version, even compatibility layers (WINE), emulations, and reverse engineered (like ReactOS).
  - Any kinds of bridge pretty much. That includes [jbridge](https://jstuff.wordpress.com/jbridge/), VSTHost's bridge, [Carla](https://kx.studio/Applications:Carla)'s Bridge, etc.
  - If the plugin is 32-bit only, then use 32-bit host! Falcosoft 32-bit, and VSTHost x86 e.g.
  - Because often times important messages like SysEx Reset failed to transmit, resulting in 
    - no reset, 
    - & **missing drums for many no SysEx Reset & no Drum program set MIDI files**.
  - in Linux case, compatible & working options have shrunk significantly, 
    - because these bridges are often times exclusively designed & tested on that Windows.
    - VST2 itself is Windows only (very allegedly). Only by the VST3 that's now cross platform. Bruh, Steinberg 😞 wtf..
    - Other programmers could only make bridge as so just to get it working. Other details are haaaaaard!.
  - Took me years to figure out why, and this is one of the culprit that broke my MIDI experience. \
    - Sorry, J, looks like you're out of the game now.
    - Btw, J, why not you put that on Steam (or better, GOG and/or itch.io)? I disliked the current checkout system here, quite unreliable.
      - No!-no!-No, yess I know. But listen. World's changed. Gabe had proven, good service, invites appreciation compared to cowardice, trust me!.
      - Yes pls, put that on Steam will ya? Promise I'll buy it, **again**. 
      - At least as a souvenir, no offense.
- Use `GS` reset by default
  - Steps
    1. Top left Menu
    2. `SysEx Options`
    3. `Reset Type`
    4. choose **`GS`**
  - Because most of the time, MIDI would go towards this Roland GS, either because 
    - many composers assumes SoundCanvas SC-55 and so on, 
    - or the most common, since Roland was the one that started the whole MIDI idea in the first place.
  - Highest chance after all went to `GS`, at General MIDI Level 1.
  - The GM2 is new and would take another century for the GS be replaced.

### Update Failed

If an update failed, chances are, there are unexpected lingering file usage that prevented the updater from replacing the files.

- Make sure the whole host is really terminated, each & every of them
- Restart your whole machine if necessary
- Check, if you had a daemon that uses any of your chosen Hybrid. End those processes if there are any.
- If your rice is way too complicated, you can use another OS image / Recovery / WinPE that has PowerShell or portable PowerShell, just to run the updater.
- Or maybe re-extract the full package, overwriting everything again?