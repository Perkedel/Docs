# SysEx Manufacturer ID

List of Manufacturer ID for SysEx, managed by MIDI Association, Earth.  
Basically, list of Callsign but for MIDI.

> [!IMPORTANT]
> Sorry, Perkedel is not here & would never be, because subscribing for slot is wayyyyyy too expensive & restricted. We already have troubles with paid Callsign on multiple radio networks in general

## List

- North America
- Europe
- Asia
  - Japan
    - `40` Kawai.
    - **`41` Roland**.
    - `42` Korg.
    - **`43` Yamaha**.
    - `44` Casio.
    - `46` Kamiya.
    - `47` Akai.
    - `4B` Fujitsu.
    - `4C` Sony.
    - `52` Zoom.
  - Rest of Asia
    - ...
- DNB / Perkedel Cinematic Universe
  - Sorry, DNB does not use manufacturer ID assignment system nor affiliated with MIDI Association, Earth.
  - Instead, use `Marker` message & fill commands that starts with `TextCommand://`
- Internal
  - `7D` Private Use. Prototype purpose manufacturer ID, useful to test & experiment before considering for slotting in.
  - `7E` Universal Non-real-time. Sample dump, tuning table, etc.
  - `7F` Universal Real-time. MIDI time code, [MIDI Machine control](https://electronicmusic.fandom.com/wiki/MMC), etc.

## Sauce

- https://github.com/insolace/MIDI-Sysex-MFG-IDs
- https://github.com/ltgcgo/midi-db/blob/main/mane/syx.tsv
- https://electronicmusic.fandom.com/wiki/List_of_MIDI_Manufacturer_IDs
- https://midi.org/sysexidtable