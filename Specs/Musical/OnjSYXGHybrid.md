# Andre Louis' S-YXG Hybrids

Andre Louis made Preservation for S-YXG VSTi series & other Yamaha instrument modules. Yes, that guy, the guy known for [Phone Ringtone archiving](https://3.onj.me/phonetones/), now also made it this!

## Download

### Choose Your Favourite!

- [S-YXG2006LE Hybrid](https://github.com/OnjLouis/syxg2026-hybrid) **RECOMMENDED 👍👍👍👍👍**. S-YXG2006LE with PVL & SG, & fallback of S-YXG50 (for voices missing in 2006LE).
- [S-YXG100 Hybrid](https://github.com/OnjLouis/syxg100-hybrid). S-YXG50 with PVL & SG, to become alike of S-YXG100PVL, **without the need of Win9x** anymore.
- [S-MU2000 Hybrid](https://github.com/OnjLouis/mu2026-hybrid). S-MU2000 with PVL & SG (not through PLG of course), with gap-only fallback of S-YXG2006LE. S-MU2000 is the priority, where the 2006LE last priority for fallbacks, and no S-YXG50 (because everything already has started from that MU2000).

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

### Demo & Custom Song

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
  - You must exactly use Veg's original yoink, not JayB's or any other mod
  - Because the tool converts the `.dll` through Reverse Engineering Binary Traversal way! So it has to be exactly Veg's file!
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
6. Wait until finish
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