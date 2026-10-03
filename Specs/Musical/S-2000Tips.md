# Tarboh's S-2000 Tips

Tips to enhance your MAME MU2000 (EX)

## Download Source Code

https://github.com/tarboh/S-MU2000

- Build
  - See https://github.com/tarboh/S-MU2000/blob/main/doc/manual.en.md
  - Just clone and go inside the project
  ```console
  $ cd Projects  # go to Projects (built-in XDG spec new 2026) folder
  $ mkdir vst_clone && cd vst_clone  # have habit to tidy up
  $ git clone https://github.com/tarboh/S-MU2000.git  # clone now
  $ cd S-MU2000  # get inside now!
  ```
  - Windows, Linux, macOS can Build now using `make`
  ```console
  $ make -j8
  ```
  - If you have `nproc` available, you can use that to automatically count all threads you got as it outputs numbers of thread. Even better, replace the `8` with `nproc`
  ```console
  $ make -j$(nproc)
  ```
  - Your build folder will appear right in this project according to your OS
    - `build`. Windows
    - `build-linux` Linux
    - `build-max` (?) macOS
  - Prep your ROMS! [See this](https://github.com/tarboh/S-MU2000/blob/main/doc/dump/README.md)
    - Program Flash! Extract from [Yamaha's Official Firmware Update](https://jp.yamaha.com/support/updates/mu2r1_uw.html)
      - The extractor tool is included. Extract the firmware update, and bring 2 parts of `.ydl` together as such, and extract
      ```console
      $ python tools/dump/ydl_extract.py part1/images/v200U12k.ydl part2/images/v200u22k.ydl \
             -o roms/mu2000_flash.bin
      ```
      - make really sure that this `mu2000_flash.bin` is in the `(PROJECT_S-MU2000)/roms`
    - ROM Dump. 
      - Above firmware update only has programs, not the entire ROM. 
      - Obtain either through existing MU-2000 or Search up `Yamaha MU-2000 ROM`. You should find it there, sorry can't DL link directly rn. 
      - Once you got the website, choose the `Standalone set` which contain all files needed pre-packed.
      - Put these ROM files in total, in the structure as shown
        - `roms/`
            - `mu2000_flash.bin` Program ROM
            - `dump/` Wave ROM, 4 x 8 MB
                - `xv364a0.ic49` 
                - `mu.....-..bin`
                - etc. `.ic....`, all the `.ic` stuffs be here!
            - `standin/`
              - `sin-table.bin` sine table used by the MEG
            - `hd44780u_b03.bin` LCD ROM. If you forgot or put not in `roms/` here exactly, the screen will be blank!
  - Install the rendered plugins!
    - `make install-vst3` will install the VST3 plugin to your VST3 library folder according to your OS
      - `~/.vst3` Linux
    - `make install-clap` will install the CLAP plugin to your CLAP library folder according to your OS
      - `~/.clap` Linux
- Run
  - Once you have successfully set it up, you can now run it
  - Standalone GUI
    - Run the app pointing to where the roms are, e.g.
    ```console
    $ build-linux/gui roms/
    ```

## Manual

- [Archive.org](https://archive.org/details/manualsbase-id-224151)
- [Emulator Manual English](https://github.com/tarboh/S-MU2000/blob/main/doc/manual.en.md)

## Key Basics

- Right Set. Right most Button
  - `PART` (Keyboard `[` & `]`). Selects your MIDI channel / track. 
    - Press both = `ALL`, view master MIDI settings
      - The All Reverb & Chorus settings are the `Rtn`.
      - The All Volume & Expression are called `Master Volume ` & `Master Attenuation` respectively.
      - **There is no Balance (All Pan)**
      - Key Shift becomes `Transpose`. It can go all the way to 24 semitones both ways (`+/-`).
  - `SELECT`. Menu selection left & right. 
    - In `PLAY` screen, it cycles through MIDI settings. 
      - Notice the little `🔻` between the meters & the VU, that is your selected variable. 
      - For selection at Bitmap display, the `🔻` actually points at the `BANK` and/or `PGM#`, as you can see on the printed label.
  - `VALUE` (Keyboard `-` & `=`). Adjust value of a variable, e.g. in main screen `PLAY` changes your `BANK/PGM#`
- Middle Set. Between lit & Right set
  - `MUTE/SOLO`. Cycles between Mute this channel, solo this channel, and back to normal.
  - `ENTER` (Keyboard `Return`). Enter certain menu
  - `EXIT` (Keyboard `Backspace`). Go back one step, or if nothing else, returns to `PLAY` screen.
- Lit buttons. These basically are Menu screen selections.
  - `PLAY` (Keyboard `A`). Your main screen. You can see VU, Patch and Banks, Bitmap, etc. Press again to cycle between different overview of the channels.
  - `EDIT` (Keyboard `E`).
  - `UTIL` (Keyboard `U`). Go to system settings & utilities
  - `EFFECT` (Keyboard `F`). See the effects setting
  - `SAMPLING` (Keyboard `M`). See the voice sampling stuffs
  - `SEQ` (Keyboard `Q`). View Song data sequences & play some, including Demo songs
- White button between Dial & Instrument Categories
  - `SELECTION`. Cycle between Sampled Voice, (PLG Modules?), & Regular Patch set.
  - `AUDITION`. Preview selected Patch. Like pressing Volume knob on some SoundCanvas modules. By default presses `C` note, but can be changed.
- Instrument Category Selector
  - Underneath the display is your instrument selectors
  - Press which to set it to first instrument of that category
  - Press again to cycle through different instrument in the category.
  - You can also cycle through all instruments using dial or `VALUE` buttons.
- Jacks & DINs
  - Microphone Jacks
    - On your left, you have 2 MIC inputs: `1` & `2`.
    - Adjust gain using `A/D INPUT` knob there.
  - MIDI Input DINs
    - You have 4 Inputs. `A` front, and the rest 3 back (Not shown in emu).
  - Headphone Jack
    - `PHONES`. Connect to your Headphone. In this emu, it lets you select audio output device.
- Knobs & Dials
  - `A/D INPUT`. Adjust gain of MIC IN jacks
  - `VOLUME`. Master volume, like all those Yamaha instruments
  - Big White Dial (Mouse Scroll). Equivalent to `VALUE`. In this emu, drag up to CW, and down to CCW.
- Memory Slot
  - `3.3V CARD`. SmartMedia slot that contains your MIDI & other data. Click to view its option. You can also directly play a single MIDI file here.

## Try out Demo!

1. `SEQ`
2. `SELECT >` multiple times until you selected `DEMO`
3. `ENTER` to load the demo songs
4. Wait.
5. Select which song to play. `ALL SONG` is playlist of all 3 songs. While you can also choose just one
6. Press `ENTER` to play selected song
7. The Demo song will play Repeat One. `EXIT` to stop and go back to Demo selection again.
8. To exit out of Demo, `EXIT` again in the demo song selection menu.

## Play custom song.

- Click on the `3.2V SmartMedia` Card slot below `MIDI IN` port. You can choose whether to create and use SmartMedia image, or directly load MIDI file.
- Directly Load MIDI file
  - `Play a MIDI file`
  - Choose your favourite `.MID` to play
  - Once loaded, the S-MU2000 will play the file immediately.
- Fun Play Facts
  - You cannot directly load some of the [MU-2000 Demo MIDI](https://github.com/ltgcgo/midi-data/tree/main/vendor/yamaha/mu) itself, especially the `R-love.mid` & `R-loveLM.mid`, because the **voice samples are accessible only through official Demo mode**. Attempting to play anyway results those to become minus one / instrumental (if there's no voice ever sampled here).
  - Some of the [demo MIDIs that you can have](https://github.com/ltgcgo/midi-data/tree/main/vendor/yamaha) may require serveral addon cards, called `PLG` Modules. Unfortunately, there's no way to achieve that in this emu atm.
    - e.g., to play VL Songs, you will need PLG-VL, & to play Singing SG Songs, you need PLG-SG. There are more PLG cards for more extra patches.
    - In today's time, you just purchase or download expansion packages digitally through [Yamaha Musicsoft at Expansion Package section](https://shop.usa.yamaha.com/en/c/downloadables/sound-expansion-library/premium-packs-voices).