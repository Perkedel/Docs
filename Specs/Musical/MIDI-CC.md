# MIDI Control Changes

## Highlight

- **0 (Bank Select MSB)**. Select Bank of the voice / patch
  - **32 (Bank Select LSB)**. Select LSB of the voice / patch
    - Roland GS,
      - LSB 0 = Default Latest / Selected. **RECOMMENDED**
        - Choose this to choose the latest version of voice maps
        - On LeekSpinner, it'll emulate SC-8850 in that GS mode.
      - LSB 1 = SC-55
      - LSB 2 = SC-88
      - LSB 3 = SC-88Pro
      - LSB 4 = SC-8850
      - in LeekSpinner, choosing `GS` reset will engage 88emu Roland SC-8850 & switch all channels to it.
        - Falls back to Free SFe.
      - You can mix & match per channel of what patch & the map to use.
  - Instrument Maps
    - 0 = Default
    - 121 = GM2 Instrumental
    - 120 = GM2 Drum
    - Roland Since SD-90
      - Instrumental
        - 80 = Special 1
        - 81 = Special 2
        - 96 = Classical
        - 97 = Contemporary
        - 98 = Solo
        - 99 = Enhanced
      - Drum
        - 104 = Classical
        - 105 = Contemporary
        - 106 = Solo
        - 107 = Enhanced
    - Yamaha
    - Van Elektronische
      - You can switch using TextCommand
        - Bankpath
          ```txt
          TextCommand://midi.bank("msb_address_id/lsb_address_id");
          ```
        - Number. MSB & then LSB, both unsigned integer.
          ```txt
          TextCommand://midi.bank(0,0);
          ```
      - Instrumental
        - ?? / `special1` = Special LeekSpinner 1
        - ?? / `special2` = Special LeekSpinner 2
        - ?? / `retro` = Pixel Retro
          - Basically plagiarism of Gashisoft's GXSCC
          - LSB selects the sound set
            - LSB 0 / `retro/scc` = SCC / Default
            - LSB 1 / `retro/famicom` = Famicom-like
            - LSB 2 / `retro/opl` = Yamaha OPL-like
            - LSB 3 / `retro/bawami` = Robbi-985 BaWaMi like
        - ?? / `novelty` = Novelty
        - ?? / `singvoice1` = SingVoice TTS 1
          - LSB sets sub-variant of selected TTS voice, e.g., from `Hatsune Miku` has `Hatsune Miku Dark`
            - LSB 0 = Default
            - LSB 1 = Append
            - LSB 2 = Dark
            - LSB 3 = Light
            - LSB 4 = Matured
            - LSB 5 = Juvenile'd
        - ?? / `singvoice2` = SingVoice TTS 2
          - LSB sets sub-variant of selected TTS voice, e.g. from `Kasane Teto` has `Kasane Teto Dark`
        - ?? / `user1` = Private User Space 1
        - ?? / `user2` = Private User Space 2
        - ?? / `user3` = Private User Space 3
        - ?? / `user4` = Private User Space 4
      - Drums
        - ?? = Pixel Retro
        - ?? = Novelty
        - ?? = Fetish ASMR SFX's
    - S Christian Collin
      <!--- 8 = Extras GS-->
      - 11 = Special GeneralUser 1
      - 12 = Special GeneralUser 2
  - In total we have `MSB:LSB:Prog`.
- **1 (Modulation)**. The one that causes output be waavyy. Represented with Right circle growing vertically
- 2 (Breath). Heavy use in Windpipe voices & Yamaha PVL. Represented with right pointing triangle growing from left
  - Build this graph based on **Respiratory core (Lung-Diaphragm)**, not perceived blow off the mouth. 
  - So on Onj's Hybrid, the left needle grows constant,
  - while on Octavia Cambiare with same file(?), the needle mixes with Velocity and other CC's giving visual sensation of player blowing into the instrument & pressure drops as they keyed in.
- **7 (Volume)**. Channel volume.
  - Only use this for perceived audio adjustment
  - For expressions & after-touch ASMR, **consider using CC 11, Expression**.
- **10 (Pan)**. Speaker balance of this channel / position relative to stereo speaker space. Lower is left, and higher is right. `64` = center
- 11 (Expression). How alive the output it. Full means 100% from Volume, lower dims the output. ~~Represented as note opacity, lower it is, more translucent until it's gone invisible.~~
  - Best used for simple ASMR to add expressions. e.g. Hard velocity, quitening, and relouding, just like that.
  - Some Yamaha VL patches do not use this, rather instead CC 2 Breath, or even CC 1 Modulation. consult manual!
- Pedals
  - **64 (Sustain)**. Sustain pedal of this channel. \<\= `0` = `OFF`, \< `64` = `ON` (Binary). If `ON`, lingering notes are represented as stroke only which stays until sustain is dropped (\> 64)
  - 65 (Portamento). Set channel to sliding note mode, where changing note firstly slide smoothly throughout frequencies before going to target.
    - 84 (Portamento Control). Amount of Portamento. Controls how long this note slides. Higher the longer before it reaches target.
  - 66 (Sustenuto). The Second Pedal. Like sustain, but only sustain last held note by the time Sustenuto active, leaving rest unsustained.
  - 67 (Una Corda). Soft Pedal / Third Pedal. On piano, it slides the hammer a little so it would hit just one wire (hence the name Una Corda (One Wire)) for all. Rest of voices would simply lower the volume.
  - 68 (Legato).
  - 69 (Hold alt.).
- Sound
  - 71 (Resonance Filter)
  - 72 (Release Time). How long the note completely fades once released. Higher the longer is.
  - 73 (Attack Time). How long the note will reach peak amplitude. Higher the longer is.
  - 74 (Frequency Cutoff). How blurry is the sound. Represented as note opacity (?). **Low-pass filter**, cuts off treble, removing the highs.
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
  - 254??? `0xFE` (Active Sense). Constant data sent from device, host, or both, usually every 300ms for `heartbeat`. To monitor connection between host and device, and if it's gone, the host and device should engage MIDI Panik (All notes Off) instead of leaving stuck notes.
 
## Sauces

- https://nickfever.com/music/midi-cc-list
- https://cdn.roland.com/assets/media/pdf/SC-8850_OM.pdf
- https://static.roland.com/assets/media/pdf/SD-90_OM.pdf