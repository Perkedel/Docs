# Basics of SysEx

## Format

MIDI messages in general are written / represented in **Hex** code (`0x..`). The one that has Number `0`-`9`, followed by partial alphabet `A`-`F`.

To make that easier & readable, these hex letters on a message, are divided by 2. Just like Hex editors.

```txt
F0AAAA....F7   From this,
F0 AA AA AA .. .. F7  To this.
```
Either way of insertions are fine, and many MIDI editors should usually trim out spaces.

With that division said, when we're talking about values, if a division means the value of it, a `00` means zero, all the way up to `FF` which means 255, See [here](https://forum/renoise.com/t/hexadecimal-how-does-ff-255/) & [reddit](https://reddit.com/r/askmath/s/KIpi2eFYYA)

## Structure

Write SysEx making sure to have a complete start `F0` and the beginning, & `F7` in the end, such as

```txt
F0 AA AA AA AA AA AA .. .. .. .. F7
```