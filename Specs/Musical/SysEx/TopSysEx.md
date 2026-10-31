# Top SysEx's

Famous System Exclusive messages common on MIDI & the files

## List

- Resets
  - Pre-GM & Non-GM
    - `` Yamaha DOC (Disk Orchestra Collection).
    - **`F0 41 10 16 12 7F 01 F7` Roland MT-32**.
  - General MIDI 1
    - **`F0 7E 7F 09 01 F7` GM ON**.
    - `F0 7E 7F 09 02 F7` GM OFF.
    - **`F0 43 10 4C 00 00 7E 00 F7` Yamaha XG**.
    - `F0 41 10 16 12 7F 01 F7` Roland MT-32.
    - **`F0 41 10 42 12 40 00 7F 00 41 F7` Roland GS**.
    - `F0 41 10 42 12 00 00 7F 00 01 F7` Roland SC-88.
    - `F0 50 2C 20 7E 1F 00 00 7F 00 F7` Korg NX.
    - `F0 40 00 10 00 08 00 00 00 00 00 F7`. Kawai GMega. ????
  - General MIDI 2
    - **`F0 7E 7F 09 03 F7` GM2 ON**.
    - `` Roland SD.
    - `` Roland HyperCanvas ON.
    - `` Korg PA.
    - `` Korg KROSS 2.
- Manipulation
  - Roland
    - Part Mode
      - ⚠️ CAUTION! You cannot have a channel use the same drum map!
        - E.g., if you have Part 10 & 12 goes to Drum 1, **Both will always select the same drum**, no matter either program and bank changes.
        - Instead, the Part 10 should stay on Drum 1, and then the second goes to Drum 2.
        - See Page 55 of [SC-8850 manual](https://cdn.roland.com/assets/media/pdf/SC-8850_OM.pdf)!
      - `F0 41 10 42 12 [40 1x 15] [..] [..] F7`
        - Address = `[40 1x 15]`
        - `x` = Part number. Hex `0` 1, `1` 2, ..., `A` 11, ..., `F` 16.
          - `0` = 1
          - `1` = 2
          - `2` = 3
          - `3` = 4
          - `4` = 5
          - `5` = 6
          - `6` = 7
          - `7` = 8
          - `8` = 9
          - `9` = 10
          - `A` = 11
          - `B` = 12
          - `C` = 13
          - `D` = 14
          - `E` = 15
          - `F` = 16
          - Hex starts from `0`, and therefore Part 1.
          - Ends at `F` meaning Part 16
        - `[..]` Data
          - `00` = Normal
          - `01` = Drum 1
          - `02` = Drum 2
        - Checksum
          - 128 - ((Combine Address + Combine data) mod 128)
      - Example
        - Set Ch. 11 to Drum1
          - Address `40 1A 15` Combine = 64 + 26 + 21 = 111
          - Data `01` Combine = 1 = 1
          - Checksum = 111 + 1 = 112; 112 mod 128 = 112; 128 (const) - 112 = 16 = Hex `10`
          - `F0 41 10 42 12 40 1A 15 01 10 F7`
        - Set Ch. 12 to Drum1
          - Address `40 1B 15` Combine = 64 + 27 + 21 = 112
          - Data `01` Combine = 1 = 1
          - Checksum = 112 + 1 = 113; 113 mod 128 = 113; 128 (const) - 113 = 15 = Hex `0F`
          - `F0 41 10 42 12 40 1B 15 01 0F F7`
        - Set Ch. 4 to Drum1
          - Address `40 1B 15`
        - Set Ch. 12 to Drum2
          - Address `40 1B 15` Combine = 64 + 27 + 21 = 112
          - Data `02` Combine = 2 = 2
          - Checksum = 112 + 2 = 114; 114 mod 128 = 114; 128 (const) - 114 = 14 = Hex `0E`
          - `F0 41 10 42 12 40 1B 15 02 0E F7`

## Extra

- Perkedel does not do SysEx because buying standard subscription is expensive!
  - Instead, we use `TextCommand://` started Marker message
  - to set reset into LeekSpinner, send `GM2 ON` (`F0 7E 7F 09 03 F7`) followed by Marker / Text message containing
  ```txt
  TextCommand://midi.reset("leekspinner")
  ```
  - Maintain the typical `GM2 ON` SysEx reset on the file as always just in case.
    - While the above TextCommand alone already means GM2 & LeekSpinner reset, You may play our MIDI files outside LeekSpinner keyboards and hence will always need to atleast have the compatibility, which includes the SysEx reset. 

## Sauce

- [Octavia](https://gh.ltgc.cc/octavia/test/)
- [Falcosoft Soundfont MIDI Player](http://falcosoft.hu/softwares.html#midiplayer)
- [MIDITester](https://openmidiproject.opal.ne.jp/MIDITester_en.html) & [Sekaiju](https://openmidiproject.opal.ne.jp/Sekaiju_en.html)
- [MIDI Forum](https://midi.org/community/midi-specifications/generic-sysex-reset-device-id)