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