# MIDI Control Changes

## Highlight

- **0 (Bank Select)**. Select Bank of the voice / patch
- **1 (Modulation)**. The one that causes output be waavyy. Represented with Right circle growing vertically
- 2 (Breath). Heavy use in Windpipe voices & Yamaha PVL. Represented with right pointing triangle growing from left
- 7 (Volume). Channel volume.
- 10 (Pan). Speaker balance of this channel / position relative to stereo speaker space. Lower is left, and higher is right. `64` = center
- 11 (Expression). How alive the output it. Full means 100% from Volume, lower dims the output. ~~Represented as note opacity, lower it is, more translucent until it's gone invisible.~~
- Pedals
  - **64 (Sustain)**. Sustain pedal of this channel. \<\= `0` = `OFF`, \< `64` = `ON` (Binary). If `ON`, lingering notes are represented as stroke only which stays until sustain is dropped (\> 64)
  - 65 (Portamento). Set channel to sliding note mode, where changing note firstly slide smoothly throughout frequencies before going to target.
    - 84 (Portamento Control). Amount of Portamento. Controls how long this note slides. Higher the longer before it reaches target.
  - 66 (Sustenuto). The third pedal. Like sustain, but only sustain last held note by the time Sustenuto active, leaving rest unsustained.
  - 67 (Una Corda). Soft Pedal. On piano, it slides the hammer a little so it would hit just one wire (hence the name Una Corda (One Wire)) for all. Rest of voices would simply lower the volume.
  - 68 (Legato).
  - 69 (Hold alt.).
- Sound
  - 71 (Resonance Filter)
  - 72 (Release Time). How long the note completely fades once released. Higher the longer is.
  - 73 (Attack Time). How long the note will reach peak amplitude. Higher the longer is.
  - 74 (Frequency Cutoff). How blury is the sound. Represented as note opacity,
  - AAAA
  - 91 (Reverb). Size of the room
  - 92 (Tremolo).
  - 93 (Chorus). Multipliyingness
  - 94 (Detune).
  - 95 (Phaser).
- Meta
  - 120 (All Sound Off).
  - 121 (Reset All CC)
  - 123 (All Notes Off). MIDI Panik
  - 126 (Monophonic Mode). Set channel to Monophonic mode 
  - 127 (Polyphonic Mode). Set channel to Polyphonic mode
  - ??? `0xFE` (Active Sense). Constant data sent from device, host, or both, usually every 300ms for `heartbeat`. To monitor connection between host and device, and if it's gone, the host and device should engage MIDI Panik (All notes Off) instead of leaving stuck notes.
 
## Sauces

- https://nickfever.com/music/midi-cc-list