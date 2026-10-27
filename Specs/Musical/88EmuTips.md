# The Usual Suspect's 88Emu Tips

Top Tips to enhance MAME Combinations of Roland SoundCanvas series.

## Download

https://theusualsuspects.io/downloads/88emuplayer

- Setup
  - Installer available! See [this guide](https://theusualsuspects.io/docs/installation-guide) for detailed info!
    - Arch btw available!
      - Add now & sign
        ```console
        $ curl -fsSL https://download.opensuse.org/repositories/home:/theusualsuspects/Arch/x86_64/home_theusualsuspects_Arch.key | sudo pacman-key --add -

        $ sudo pacman-key --lsign-key 6F616D60DB991ED61A6F29B0006C0F47711C6743
        ```
      - Add this repo into `/etc/pacman.conf
        ```conf
        [home_theusualsuspects_Arch]
        Server = https://download.opensuse.org/repositories/home:/theusualsuspects/Arch/$arch
        ```
      - Install Now! Will take from that `home_theusualsuspects_Arch` personal repository, not AUR.
        ```console
        $ paru -Sy theusualsuspects-88emu
        ```
  - Prep Your ROMs!
    - Sorry, can't DL link right now. You can instead look it up yourself from various source.
    - ROMs should be in `.bin` format and as such. **Never is `.exe`!**
    - It is recommended to obtain `Standalone Package` to make it easier.
    - Drop everything (even the subfolder) into
      - Linux: `~/.local/share/The Usual Suspects/88emuPlayer/roms`
      - Windows: `My Documents\The Usual Suspects\88emuPlayer\roms`
    - 88emu will look & match these ROM files by MD5 Hash, even crawls down to subfolders. Alternatively, you can try matching the filename & size according to Missing ROM dialog pop up.
- Run
  - Standalone
    - Simply run its binary. 88Emu Player will fetch ROM files from above ROMs directory.
  - Plugins
    - Load whichever compatible plugin formats into your Host. There are
      - CLAP **(BEST OF THE BEST)**. Newer Open Source Plugin Format from [CleverAudio](https://cleveraudio.org/).
      - LV2. [LADSPA v2](https://lv2plug.in/), Open Source plugin format.
      - VST3 VSTi. Steinberg latest VST version
      - VST2 VSTi. Reverse engineered Steinberg's VST2 via [FST](https://github.com/pierreguillot/FTS).
      - AU3. Apple Audio Unit

## Key Basics

- Machine Selection
  - Choose your device of various Roland SoundCanvas evolutions.
  - Located on bottom left corner dropdown.
- Playlist
  - Not to be confused with SoundBrush, but basically works the same, to inject MIDI playback into your module emulation.
  - It is a playlist that list your MIDI to be played in that order
  - At the time of writing, Playlist can only keep playing all song until the end of the playlist.
  - Drag & Drop or Open a MIDI file to add it there.
  - Right click
    - `Load Playlist`. Load a playlist file
    - `Save Playlist`. Save this playlist into a list file. Each line is an absolute path to each MIDI file.
    - `Clear Playlist`. Clear the whole playlist.
  - Buttons
    - `⏯️`. Play the song if hasn't playing. Pause if playing.
    - `⏹️`. Stop the Song
- Volume Knob
  - Adjusts how loud audio output to be. For this emu situation, it is best to set it to MAX, since it'll be typically 0 dB attenuation at your sound device.
    - Note however, this obviously does not always apply IRL, as you must be careful adjusting your volume. Carelessly increasing volume may damage your audio equipment and even cause deafness!
  - `▶️ PREVIEW` (Keyboard `Tab`). Preview currently selected patch. Since pressing volume knob is unavailable in this emu, you will instead have this new button as a replacement.
    - Only available since SC-88 (except VL).
- Display
  - Displays information of your MIDI experience
  - On some module evolution, some MIDI files can inject special SysEx such as Bitmap & Title Text to it.
- Buttons & Dials
  - Power ON/OFF (Keyboard `Q`). Toggle power state of the module.
    - SC-55, SC-55mkII, SC-155, SC-155mkII, & SC-88VL power are digital. That's because to make it work with its remote control Canvas-Brush combo.
      - For these digital power system, you can unplug them from power using `Shift` + `Q` to emulate those of mechanical power switch. 
    - The rests are typical Mechanical Open-Close toggle switch.
  - MT-32, CM-32L, CM-64
    - `PART` `1` - `5` (Top row `1` - `5`). Five Part buttons
    - `RHYTHM` (`R`).
    - `SOUND GROUP` (`G`).
    - `SOUND` (`S`).
    - `VOLUME` (`V`). Set adjustment into Channel Volume.
    - `MASTER VOLUME` (`M`). Set adjustment into Master Volume.
    - Volume Knob. Rotaty Encoder with press button, sets volume, value, or navigate menus based on current menu at.
    - **CM-32P is empty of switches** but volume knob.
  - SC-55, SC-88, Pro, VL
    - Bar Lit
      - `ALL` (Keyboard `W`). Overview master MIDI settings. You can also adjust some of the following Manipulatable MIDI Master settings below.
      - `MUTE` (Keyboard `E`). Mute currently selected Channel
      - `🔺 SC-55 MAP` (Keyboard `1`). (Since SC-88) Set instrument map into SC-55 / Up navigation
      - `🔻 EQ` (Keyboard `2`). (SC-88 Only) Toggle Equalizer? / Down navigation
      - `🔻 SC-88 MAP` (Keyboard `2`). (Since SC-88Pro) Set instrument map into SC-88 non-Pro / Down navigation
    - Manipulation
      - `PART` (Keyboard `R` & `T`). Selects Channel to view.
        - Press both to do the following
          - SC-55 OG, 155 OG
            - Opens Advanced setting.
              - Part mode: Normal, Drum 1, Drum 2.
              - etc.
              - Navigate between the settings Up & Down, using `ALL` & `MUTE`
            - Initialize SysEx Reset. See Below for detail
          - SC-55 mkII, 155 mkII
            - Opens Advanced setting.
              - Navigate between the settings Up & Down, using `🔺 SC-55 MAP` & `🔻 SC-88 MAP` (on SC-88 non-Pro it's `🔻 EQ`)
              - The `ALL` becomes set Advanced Master Settings, & `MUTE` returns to normal function.
            - Demo Mode (Since SC-55 mkII & SC-155 mkII). See section below for details!
      - `INSTRUMENT` (Keyboard `Y` & `U`). Selects Patch on that Channel.
      - `LEVEL` (Keyboard `P` & `[`). Adjust Volume (CC ???) of the Channel.
      - `PAN` (Keyboard `D` & `F`). Adjust Balance (CC ???) of the Channel. Where between the 2 speakers, this instrument sits at?
      - `REVERB` (Keyboard `G` & `H`). Adjust Reverb of the Channel. How wide the volume-size this room to be?
      - `CHORUS` (Keyboard `J` & `K`). Adjust Chorus of the Channel. How much the sound wave duplicates back to listener?
      - `KEY SHIFT` (Keyboard `I` & `O`). Pitch bend of the Channel.
        - Press both to set `DELAY`s. 
          - `KEY SHIFT` to adjust
          - `PART` to switch channel to adjust
          - Press both `KEY SHIFT` again to apply & exit. 
      - `MIDI CH` (Keyboard `A` & `S`). Idk what is this, I thought it changes where MIDI Channel it outputs to, but if `MIDI CH` is not same as the Channel, it'll play both this & that MIDI Channel.
    - Insertion Effects (Since SC-88, except VL)
      - `USER INST ON/OFF` / `EFX` (Keyboard `3`). ~~Toggle between in-MIDI Effect and User-made Effect~~ Toggle Effect On/Off (???).
        - On SC-88Pro, it becomes `EFX`. Here, you can select hundred kinds of insertion effects.
        - You can only have 1 kind of effects, and channel you chose to have one (`EFX` lit on SCVA), will possess only the same selected EFX.
      - `EFFECT SELECT` (Keyboard `4`). Select Effect aspect to adjust. Note the red `▶️` LEDs cycling through as you press. It points to effect variable set according to printed label there.
      - Adjustment
        - `DELAY` / `EFX TYPE` (Keyboard `Z` & `X`). Adjust above selected effect variable / Type of EFX. If no red `▶️` LED selected & EFX is OFF, it adjusts `DELAY`
        - `INSTRUMENT` / `EFX PARAM` (Keyboard `C` & `V`). Adjust above selected effect variable / Parameter of the chosen EFX. If no red `▶️` LED selected & EFX is OFF, it acts like original `INSTRUMENT` buttons up right
        - `VARIATION` / `EFX VALUE` (Keyboard `B` & `N`). Adjust above selected effect variable / Value of the EFX's Parameter selected. If no red `▶️` LED selected & EFX is OFF, it adjusts Instrument variants / Bank.
  - SC-8850
    - ATM Side Buttons (Keyboard `F1` through `F4`)
      - These are `F?` buttons located underneath your display
      - The button points to respective tab at the bottom of the screen.
    - Manipulations
      - `INST MAP`. Cycle through different instrument maps.
      - `SHIFT` (Keyboard `Shift`). Hold & press another button for alternate function
      - Menus
        - `EDIT` (Keyboard `E`).
          - Press both `EDIT` & `PART ◀️` for `UTIL` menu
        - `DRUM`.
        - `EFFECTS`.
        - `UTIL` (Press both `EDIT` & `PART ◀️`)
        - `ALL` (Press both `PART` buttons)
        - Solo Mute
          - `SOLO`. Solo currently selected Channel
          - `MUTE`. Mute currently selected Channel
      - Patch Selections
        - `PART` (Keyboard `Arrow Left` & `Arrow Right). Select Channel to view
          - Press Both for `ALL` menu
        - `🔽/VAR.`. Select Bank manipulation
        - `🔼/INST.`. Select Program Number manipulation
        - Notice that the black hovers between the `VAR.` and `INST` on top left of screen there as you switched.
        - Use the Dial or `INC` & `DEC` to change selected CC number.
      - Navigation
        - Both `🔽/VAR.` & `🔼/INST.` can become Down & Up navigation respectively during menu screen
        - `EXIT` (Keyboard `Backspace`). Go back & cancel operation
        - `ENTER` (Keyboard `Return`). Confirm, Enter, & Execute Operation.
        - `VALUE` Big Black Dial (Mouse scroll / drag up-down). To change value of selected option variable. Alternatively,
          - `DEC` (Keyboard `-`). Decrease value
          - `INC` (Keyboard `=`). Increase value
  - MV30
    - ATM Side Buttons
      - `F1` - `F5` (Keyboard `F1` - `F5`). Corresponds to actions of the bottom bar of the screen
    - Tabs
      - `PLAY`. Main tab
      - `PATTERN` (Keybooard `P`)
      - `TIMBRE EDIT` (Keyboaord `T`)
      - `SYSTEM` (Keyboard `S`)
      - `DISK` (Keyboard `D`)
    - D-pad
      - Arrows (Keyboard Arrows). Up-left-down-right navigation key
      - `OK` (Keyboard `ENTER`). Confirm button
      - `EXIT` (Keyboard `ESCAPE`). Cancel / Back button
      - `JUMP` (Keyboard `Tab`). "Jump" button
      - Dial (Keyboard `-` & `=`). Value adjustment dial, with rolling on hold
      - `VALUE -` & `VALUE +` (Keyboard `Pg Down` & `Pg Up`). Value adjustment buttons
      - `SHIFT` (Keyboard `Shift`). Shift button
    - Value
      - `0` - `9` (Keyboard Number Row). Numeric Keypad
      - `INS` (Keyboard `Insert`). Insert button
      - `DEL` (Keyboard `Del`). Delete button
    - Transport
      - `START/STOP` (Keyboard `Space`). Start or Stop sequence / song loaded
    - Pedal
      - `Footswitch` (Keyboard `Ctrl`). A Pedal
  - SD-90
    - **Pls wait!, not yet exist, pls request!**
    - Digital Audio.
      - Audio Source. Selects source from the following
        - `MIC/GUITAR`. From the quarter inch `MIC/GUITAR IN` jack
        - `LINE IN`.
        - `DIGITAL IN`.
        - `TRACK DOWN`.
      - Effects. Adjusts the effects for the audio source
        - `SELECT`
        - `EDIT`
        - **`BYPASS`**. Disable effects & bypass the raw audio as is.
    - Navigation
      - `PAGE 🔺` & `PAGE 🔻`. Select Tab
      - `SYSTEM`. Go to system settings screen.
        - You can visit the demo from here by going to topmost page (Press `PAGE 🔺` repeatedly until you see `EDIROL` / `STUDIO CANVAS` on top with MIDI Parts).
    - MIDI Instruments.
      - `INST/DRUM SET`. Go to Instrument screen. Adjusts Patch & Programs of the selected MIDI Part
      - `EFFECTS`. Go to Effects screen. Adjusts effect of the MIDI Generator
      - `SHIFT` (Keyboard `Shift`)
      - `PART ◀️` & `PART ▶️`. Select MIDI Part
      - `EXIT` (Keyboard `Escape`). Cancel / Back button
      - `ENTER` (Keyboard `Enter`). Confirm button
      - `PREVIEW`. Preview current patch on selected MIDI Part
    - System Control
      - `POWER` (Keyboard `Q`)
      - `MIC/GUITAR` Jack. Open input selection menu. Choose your input device!
      - `GAIN`. Adjust gain of plugged in device
        - `MIC MODE` / Push this knob. Switch the plugged in input device mode between `MIC` or `GUITAR` mode 
        - `PEAK` LED. Lit when loudness peaks
        - `MIC GUITAR` LED. Gain indicator, indicates selected mode.
          - ON = `MIC` mode
          - OFF = `GUITAR` mode
      - `VOLUME`. System volume knob
      - `Headphone jack`. Open output selection menu. Choose your output device!
    - ATM Side Buttons / Quick Access
      - `V1` - `V3` Quick Access Knobs. 3 knobs that correspond to certain action based on your current screen.

## Manuals

- [SC-55](https://cdn.roland.com/assets/media/pdf/SC-55_OM.pdf)
- [SC-88Pro](https://cdn.roland.com/assets/media/pdf/SC-88PRO_OM.pdf)
- [SC-8850](https://cdn.roland.com/assets/media/pdf/SC-8850_OM.pdf)
- [SD-90](https://static.roland.com/assets/media/pdf/SD-90_OM.pdf)
- [88emu](https://github.com/dsp56300/gearmulator/blob/main/doc/88emu_readme.md)

## Try Demo

- SC-55, SC-155, SC-88 & Pro
  - Unfortunately there's no Demo built-in.
  - I believe, this was intended to have Roland SoundBrush next by it.
  - Alongside, you should receive a floppy disk containing the Demo songs that you insert into the SoundBrush.
  - Basically, just use the built-in Playlist feature.
- SC-55 mkII, SC-155 mkII
  1. Power off (`Q`).
  2. Hold both `PART` buttons
  3. Power on again (`Q`). You can now release both `PART`.
  4. Select which song to play using `PART`. You have
    - Moonlight Picnic
    - Low Flying
    - Supplex Hold
    - Monopoly
  5. `ALL` to play. `MUTE` to stop. **Demo always play in cycle**, i.e. Repeat All.
  6. To exit, Stop the song (`MUTE`) & then press both `PART`.
- SC-8850
  1. Keep the power on
  2. Press `EDIT` & `PART ◀️` to go to `UTIL` screen
  3. `F4` to see demo
  4. Choose your song! You have
    - Idecs - THE SECRET PLACE ft. not Something Jackson
    - Heigo Tani - WALL FIVE MIX
    - Yuuki Kato (Music Brains, inc.) - Blue X
    - *All Song*. Repeat All the whole demo.
- MV-30
  1. Make sure the system diskette is basically working. 88emu yoink pack should also have included the diskette as the ROM part file automatically detected.
  2. Go to `DISK` tab (Keyboard `D`).
  3. `Load Song` (Press `F1` or Keyboard `F1).
  4. Go down to the `N Songs on Disk` section, Press Down arrow (Keyboard Arrow down)
  5. Choose song with dial or value `-`/`+` (Keyboard `-`/`=` or `Pg Down`/`Pg Up`)
  6. `Load` which correspond with `F1`
  7. Confirm the `Are you sure` with `Load` again, which corresponds with `F1`
  8. `START/STOP` (Keyboard `Space`)
- SD-90
  1. Go to system setting, press `SYSTEM`
  2. Go to the topmost page, press `PAGE 🔺` Repeatedly, until you arrive at the Demo screen with the following
    - `EDIROL` logo / `STUDIO CANVAS` logo
    - 16 MIDI Part meters
    - Selected demo song title
    - `Play, Push ENTER`
  4. Choose your favorite demo song with `V1` Knob(?)
  3. `ENTER` to play demo now
  4. `EXIT` to stop playing
- Startup Test Mode
  - SC-88Pro Only
    1. Power Off (`Q`)
    2. Press & hold both `KEY SHIFT` buttons (`I` + `O`)
    3. Power On (`Q`)
    4. **Quickly press volume knob (`Tab` / `▶️ PREVIEW`) immediately before startup ends!**
    5. Here's what can you do
      - LED Cycle & Lit test. Press Volume knob (`Tab` / `▶️ PREVIEW`) once
    6. After done, Power cycle again (Power Off & On again) to return normal.
  - SC-88
    - Same as SC-88Pro
    - Difference being, while holding both `KEY SHIFT` buttons (`I` + `O`), Powering on (`Q`) immediately leads you to Test mode
    - LED test (Press Volume knob (`Tab` / `▶️ PREVIEW`) twice) also available
  - MT-32, CM-32L(N), CM-64
    1. Power Off (`Q`)
    2. Choose the following test!
      - System test
        1. Hold `PART 3` + `VOLUME` (Top row `3` + `V`)
        2. Power On (`Q`) & you're in the system test mode!
      - Firmware Version
        1. Hold `PART 4` + `RHYTHM` + `MASTER VOLUME` (Top row `4` + `R` + `M`)
        2. Power On (`Q`) & you're in view firmware version!
          - MT-32 2.x
            ```
            MT-32 v2.07 90-05-23
            ```
          - MT-32 1.x old
            ```
             ver 10 Oct, 87
            ```
            few seconds later,  
            ```
            Tks to Masa + Adrian
            ```
            Then returns to normal mode  
          - CM-32L(N) & CM-64
            ```
            CM32/LAPC1.02 891205
            ```
- Obtain more Demo songs!
  - [DTM-Hub Demo Data!!](https://github.com/ltgcgo/midi-data/tree/main/vendor/roland)
  - [Compare that with Octavia](https://gh.ltgc.cc/octavia/test/). Audio renders made by DTM-Hub community members.

## Play Custom Song

- Built-in Playlist
  - You can drag & drop your MIDI files into it's own built-in playlist
  - Choose a song added, and it'll immediately play it to the emulator.
  - Or press `▶️` to play now. While playing, you can pause with the same button (`⏸️`)
  - To stop playback, press `⏹️`
- MIDI Loop
  - You can use your own MIDI looper by setting the MIDI Input towards this emulator, into the MIDI Loop out of the number.
  - Then, on your external player or DAW, set the MIDI OUT to MIDI loop in, of that number.
- Plugins
  - Load 88emu as a plugin inside your Host.
  - Play or administer some MIDI messages into the loaded plugin.

## Initialize SysEx Resets

- Older SoundCanvas
  1. Power OFF
    2. If you want to change to CM-64 mode on SC-88 & Pro, keep the power ON.
  2. Hold certain keys before powering back on as follows:
    - SC-55 & SC-155
      - both `PART` / `INSTRUMENT ▶️` = Initialize GS Reset
      - `INSTRUMENT ◀️` = Initialize MT-32. Note, **this is not the same MT-32** experience unlike the OG, it's just a compatibility map.
      - both `INSTRUMENT` = Initialize All / Factory Reset, **AVOID!**, unless you know what you're doing.
    - SC-55 mkII & SC-155 mkII
      - `INSTRUMENT ▶️` = Initialize GS Reset
      - `INSTRUMENT ◀️` = Initialize MT-32. Note, **this is not the same MT-32** experience unlike the OG, it's just a compatibility map.
      - both `INSTRUMENT` = Initialize All / Factory Reset, **AVOID!**, unless you know what you're doing.
    - SC-88 & SC-88Pro
      - Keep the power on, and
      - Press both `EFFECTS SELECT` + `INSTRUMENT ◀️` = Initialize CM-64. Note, **this is not the same CM-64** experience unlike the OG, it's just a compatibility map.
    - SC-88VL
      - `INSTRUMENT ◀️` = Initialize CM-64. Note, **this is not the same CM-64** experience unlike the OG, it's just a compatibility map.
      - both `INSTRUMENT` = Initialize All / Factory Reset, **AVOID!**, unless you know what you're doing.
  3. Once you held above buttons, keep holding, and Power back on.
  5. You can see `Init XYZ` confirmation dialog, you can now release those buttons.
  4. Notice the blinking buttons. Press `ALL` to confirm, or `MUTE` to cancel.
- SC-8850
  1. Keep the power on
  2. Press `EDIT` & `PART ◀️` to go to `UTIL` screen
  3. `F3` for Init selections. Choose!:
    - `Initialize All`. Basically Factory Reset, **AVOID!**, unless you know what you're doing.
    - `Initialize GS`. Reset to Roland GS
    - `Initialize GM1`. Reset to General MIDI level 1
    - `Initialize GM2`. Reset to General MIDI level 2
    - Wait, where's the MT-32??? Eh, it'd still not be the one anyway.
    - Navigate using `🔽/VAR.` & `🔼/INST` or Dial or `INC` & `DEC`
  4. `ENTER` to select
  5. Notice the confirmation dialog. Press `ENTER` to confirm, or `EXIT` to cancel.

## Rendering

Use `88EmuCli` for rendering the MIDI songs

- Audio
  - Have a MIDI file you'd like to render.
  - `cd` into the folder where the MIDI is
  - run the command line of 88Emu to render the MIDI file fast, e.g.
    ```console
    $ 88EmuCli --device sc8850 --sample-rate 96000 --bits 32 onestop.mid --output ~/Projects/RenderMIDI/88emu/onestop.wav 
    ```
    - Render using SC-8850
    - At 96 kHz Sample Rate, 32-bit
    - of this Microsoft `Onestop.mid`
    - Into an organized render folder.
    - Rest arguments unneeded, leave default setting & ROM location there is to it.
- Video
  - Have a MIDI file you'd like to render.
  - **Install FFmpeg first, if you haven't already!** Why wouldn't you have one already?, bruh..
  - `cd` into the folder where the MIDI is
  - run the command line of 88Emu to render the MIDI file fast, e.g.
    ```console
    $ 88EmuCli --device sc88pro --video "~/Projects/RenderMIDI/88emu/onestop.mp4" --video-size 1920x1080 --fps 60 "onestop.mid"
    ```
    - Render using SC-88Pro
    - Resolution & FPS of 1080p60
    - of this Microsoft `Onestop.mid`
    - Into an organized render folder.
    - Rest arguments unneeded, leave default setting & ROM location there is to it.

## Emu Legal Shenanigans

Is your country / region / city / independent city you live in has law that outright unconditionally forbids emulation, in which of course, typically never been endorsed by the manufacturers?

Then check out this file: [Emu Legal Shenanigans Tips](Specs/Politics/EmuLegalShenanigans.md).