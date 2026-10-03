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

## Key Basics

- Right Set. Right most Button
  - `PART`. Selects your MIDI channel / track. Press both = `ALL`, view master MIDI settings
  - `SELECT`. Menu selection left & right
  - `VALUE`. Adjust value of a variable, e.g. in main screen `PLAY` changes your `BANK/PGM#`
- Middle Set. Between lit & Right set
  - `MUTE/SOLO`. Cycles between Mute this channel, solo this channel, and back to normal.
  - `ENTER`. Enter certain menu
  - `EXIT`. Go back one step, or if nothing else, returns to `PLAY` screen.
- Lit buttons. These basically are Menu screen selections.
  - `PLAY`. Your main screen. You can see VU, Patch and Banks, Bitmap, etc.
  - `EDIT`.
  - `UTIL`. Go to system settings & utilities
  - `EFFECT`. See the effects setting
  - `SAMPLING`. See the voice sampling stuffs
  - `SEQ`. View Song data, including Demo songs
- Instrument Category Selector
  - Underneath the display is your instrument selectors
  - Press which to set it to first instrument of that category
  - Press again to cycle through different instrument in the category.
  - You can also cycle through all instruments using dial or `VALUE` buttons.
- Microphone Plugs
  - On your left, you have 2 MIC inputs
  - Adjust gain using `A/D` knob there.

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