# Basic Structure

Our Kolmorottzzet are structured as follows

```
(Kolmo_type)_(disk_location)/Artistic_Setups/(AuthorName)
```

- Kolmo Types
  - `MIDI`. for MIDI files. `Artistic_Setups` shim is not necessary.
  - `kolomorotzzet_(kolmorotshitt)/Artistic_Setups`. for general files
  - Sub-Rabbithole inside `Artistic_Setups`. A non-author folder containing sub-kolmo of a specific Rabbithole
    - `Doom WADs`. Doom mods for various Source Ports
    - Commodore 64. 8-bit computer files such as diskette, apps, musics, etc. for those classic retro computers.
    - MIDI. see `MIDI` above. We already happened to make `MIDI` Rabbithole a standalone sub-kolmo Rabbithole.
- Disk Location
  - This labels where the branch of Kolmo is located at
  - e.g., this disk is labeled `Full3`, and another `Full4`.
  - The Disk location label is **not necessary on the actual disk tho**. Leave the homework folder named `kolomorotzzet_(kolmorotshitt)` on all different disks. E.g.,
    - `/mnt/Games/kolomorotzzet_(kolmorotshitt)`
    - `/mnt/LTO_0/kolomorotzzet_(kolmorotshitt)`
    - `webdav://x0p1r4t3.dnb/kolomorotzzet_(kolmorotshitt)`
- Author Name
  - Inside the `Artistic_Setups`, you make directory based on the name of the author who made the file.
  - Then put those files according to which authors.
  - [See more detail in this document](/Specs/Archival/AuthorStructure.md).