# LeekSpinner TextCommand

`TextCommand://` is a special Text / Marker syntax that will be recognized by our LeekSpinner MIDI machined & compliant-to-spec derivatives, when such message that started with `TextCommand://` has been received.

TextCommand exist to exploit fault in MIDI standard, where slotting in Hardware Manufacturer ID into the standard would cost very exorbitant. TextCommand will be the Gratis, Open Source, & FULL VERSION solution for all manufacturers building custom commands for their MIDI module

## How to TextCommand

it's easy! Simply send `Text` / `Marker` message starting with `TextCommand://` and add your commands there.

```txt
TextCommand://print("hello world");
```

The command that follows would be composed C-like, Lua-like.

### If Else Statements

All If-else statements must be immediately closed in that message, to be considered valid

```txt
TextCommand://if(a=1){print("a is true (" + 1 + ")");} // YES

TextCommand://if(b=1)print("b is true (" + 1 + ")"); // YES

TextCommand://if(a=1){
TextCommand://print("a is true (" + 1 + ")");
TextCommand://} // WRONG
```

### Comment

As such, there's no longer separated `/* */` here. Both starter & closing can only be in that message.  
Well, at this point you'd just use `//` or just use regular Marker message.

```txt
TextCommand://print("a"); /* dsakjfalsdkjf; */ print("b"); /* bla bla */ print("c"); // YES

TextCommand:///* // ERROR!
TextCommand://adfakls // ERROR!
TextCommand://*/ // ERROR!
```

### Terminator

Terminator `;` is optional, if a TextCommand **goes for just 1 command**. Otherwise, you have to have `;`.  
That includes commands inside `{}` bracketed function container.

```txt
TextCommand://print("hello world") // YES

TextCommand://print("hello world"); // YES, again, the `;` is optional if that's the only command in this message.

TextCommand://{print("hello world");} // YES, the `;` must be there, or else ERROR!
```

> [!TIP]  
> Recommended to always end function with `;` anyway for good measure 😉.

### Library

You can do import libraries ala Nim-Lua!

```txt
TextCommand://local Vocaloid = data.loadBlob("Vocaloid.lsl.zst"); // import! This variable now becomes the class instance of it
// You must put the archive next by the player binary, or system lib folder (such as `/usr/lib/leekspinner`)

TextCommand://Vocaloid.set_voicebank("miku_classic"); // and do some functions there!, such as call a function for this channel.
TextCommand://Vocaloid.bind_plg(0); // install to virtual slot!
TextCommand://midi.setMapping("plg_0"); // set voice map to Vocaloid Plugin now!

// You can also load by archive blob directly too!, all included in a single MIDI file just like AppImage
TextCommand://local Utau = data.loadBlob("Utau.lsl.zst", "oiwey9pryuioahwif....");
```

### Resources

Treat your `cache` as the root of your resource that supports foldering.

```txt
TextCommand://data.loadBlob("my_thing.tar.zst", "..."); // extract contents into `ResourcesRoot/my_thing`
TextCommand://data.loadBlob("super/my_thing2.tar.zst", "..."); // extract contents into `ResourcesRoot/super/my_thing2`
```

## Basic

### Reset!

Reset MIDI settings, initialize everything for next MIDI experience. You just need to tell what reset once, and Leekspinner shall automatically pick the base reset first (if comes from either `GM` or `GM2`), and then the target.

```txt
TextCommand://midi.reset("leekspinner"); // Reset to `GM2` & then `Van Elektronische Leekspinner`
TextCommand://midi.reset("ls"); // too long!! shorten if pls!
TextCommand://midi.reset("miku"); // This also works to, i.e. also equals to `leekspinner`
TextCommand://midi.reset("gm"); // Reset just into `GM1`
TextCommand://midi.reset("gm2"); // Reset just into `GM2`
TextCommand://midi.reset("xg"); // Reset to `GM1` & then `Yamaha XG`
TextCommand://midi.reset("gs"); // Reset to `GM` & then `Roland GS`
TextCommand://midi.reset("pa"); // Reset to `GM2` & then `Korg PA`
TextCommand://midi.reset("mt32"); // Reset to `null` & then `Roland MT-32` (Pre-GM) and engage MT-32 emulator if available, or its replica
TextCommand://midi.reset("sf2"); // Reset to `GM1` & then `Roland GS` with limitation of `E-mu Creative SoundFont`. You may lose `LSB` sliding capability anymore, unless you enabled `Use LSB on these extra SF2's` or `Disable setting constrictions`.
TextCommand://midi.reset("null"); // Reset to void. Without any of the sound on any patch, no drum even. Good for synths that doesn't even comply with any `GM` standards & its evolution whatsoever. Use `midi.asignFonts` below to build your own standard!
```

## Eye Candies & ASMR!

### Message Printer

Advanced Message print should use the intended function about it, rather than `print()` which intended only for debugging purpose.

```txt
TextCommand://Lcd.message("Hello\nWorld"); // Print to the LCD, the `Hello` on first line, and `World` below it.

TextCommand://Lcd.message("This is an extraordinary song", Lcd.NO_SCROLL); // By default, message will scroll since it's too long, 
// but with `NO_SCROLL` enum, you'll get `This is an ` for 5 sec, fancily swiped to `extraordinary`, `song`, and close message after that.
```

### Lyrics

Lyrics will be broadcasted both by `Lyrics`, `XF Lyrics`, & `Leekspinner Karaoke` at the same time. Players & Visualizers should automatically prefer the latter most sophisticated system in tier back to back.

```txt
TextCommand://Lcd.lyric("Hap"); // Be sure to build it syllable by syllable, each attached next by `Note On` e.g.
TextCommand://Lcd.lyric("py ");
TextCommand://Lcd.lyric("birth");
TextCommand://Lcd.lyric("day ");
TextCommand://Lcd.lyric("to ");
TextCommand://Lcd.lyric("you..,"); // like that, as usual
.....
```
Here's the priority, from the highest:

1. Leekspinner Karaoke
2. XF Lyrics
3. regular `Lyrics`
4. regular `Text`

### Chords

Same goes for Chords too.

```txt
TextCommand://Lcd.chord("C"); // C Major. Just type whatever you think it would be.

TextCommand://Lcd.chord("Gbm7aug"); // G flat minor 7th augmented

TextCommand://Lcd.chord("C#"); // C sharp Major. Hashtags on strings too, of course means `sharp`.

TextCommand://Lcd.chordNote("1 3 5#"); // Somekind of weird C chord. If you play by chording keys rather than perceived title, you can chord by keys too, separated by space. 
// Leekspinner can figure it out ala if you are ACMP Chording for Styles.

// To cancel chord, you can
TextCommand://Lcd.noChord(); // YES
TextCommand://Lcd.chord("cancel"); // YES
TextCommand://Lcd.chordNote("C C# E Eb"); // YES. Do it Yamaha's way
TextCommand://Lcd.chordNote("C C# E D#"); // YES. and something.
```
Again, Priority:

1. Leekspinner Chord
2. XF Chord

### Display

Send bitmap images to LCD!

`lcd.bitmap(filepath:String, fit:(enum)Lcd.Fit_Mode)` broadcasts to all kinds of machine bitmap models

```txt
TextCommand://data.loadBlob("filename.png", "a;slkdhfao;iwehrioahoighoa;erhfgohjskalfghjka...."); // Recommended to load all image blobs first,
TextCommand://lcd.bitmap("filename.png"); // and you can execute loading it to displays
// Just like how Yamaha MU transmit voice blobs through MIDI connection. See Tarboh's S-MU2000 Sampling feature if necessary.

...
TextCommand://Lcd.bitmap("bad_apple.mp4"); // Remember, the Leekspinner spec uses ffmpeg to seamlessly convert blobs to compatible formats of the target.
```
- Conversion
  - Best to draw all in color. Broadcaster should take care the rest.
  - Image frames are broadcasted Fill stretched by default.
  - If it's video or GIF, broadcaster broadcasts animatedly at another thread by FPS defined in the file blob.
  - If LCD is monochrome, use Grayscaling dither method as possible (SC-8850)! Otherwise, Half-Half Black or White method (SC legacy, MU).
- Priority:
  - Leekspinner SSTV
  - Yamaha MU
  - Roland SC-8850
  - Roland SoundCanvas Legacy
- Caveats
  - Files become as size of packed image file, effectively making `.MID` becoming `.tar`-like.
  - But, Leekspinner spec expects that you have compression methods to compress those blobs, see next section

### Compression!

Of course, you will see that the blob generator has compression section there.

- Input
  - File Browsable: `bad_apple.mp4`
- Compression
  - Algorithm: ..., `7z (Igor Pavlov)`, **`Z Standard (Facebook / Meta)`**, ...
  - Level: 1, ..., **10**, ..., 22
- Output
  - TextBox Copyable:
    ```txt
    TextCommand://lcd.loadBlob("bad_apple.mp4.zst", "asldhfauiwehiufhawiehf...........");
    ```

This is to ensure the packed file compressed & help reduce output space. Since this would make things slow to load, Leekspinner spec expects that once you understood the gist of the MIDI file, to load all blobs found into RAM, from start to finish. Then treat displayment actions (`bitmap`, `audio`, etc.) into a read-pointer-content to the loaded blob.

For realtime user, it is recommended to use level fast enough while still saving, e.g. Zstd Level 4 just like this [CachyOS's btrfs config uses](https://wiki.cachyos.org/installation/filesystem/#btrfs).

### Full Audio

Audio Synchronized play! Play whole Audio file

```txt
TextCommand://data.loadBlob("sing_tape_waifu.opus.zst", "8347298742987ufahsfhasdkjhf"); // Load the sound source

TextCommand://audio.play("sing_tape_waifu.opus.zst", 0); // At certain timestamp, play it now from the file beginning zero second!
```

### Sampled Audio

Or play it as the Soundfont letters.

```txt
TextCommand://data.loadBlob("clip_kyah_waifu.opus.zst", "...."); // Load all these clips!
TextCommand://data.loadBlob("clip_yameteKudasai_waifu.opus.zst", "....");
TextCommand://data.loadBlob("clip_ahh_waifu.opus.zst", "...."); // just like that..

// Clear the old one first, if you want, just in case
TextCommand://data.clearFonts(false); // Destroy just the custom assigned font, leave internal waves alone.
// or
TextCommand://data.loadFonts(0, true); // Load `0` which is internal waves, and purge custom assigned fonts (`purgeCurrent` = `true`)

// Then assign each of them somewhere! Filename, MSB (from `0`), LSB (from `0`), and Prog (from `1`).
TextCommand://midi.assignFont("clip_kyah_waifu.opus.zst", 97, 0, 10);
TextCommand://midi.assignFont("clip_yameteKudasai_waifu.opus.zst", 97, 0, 11);
TextCommand://midi.assignFont("clip_ahh_waifu.opus.zst", 97, 0, 12);
```

### Resources Overall

The `data.loadBlob` is very powerful! You can make `.mid` into Archive files, effectively, that's compatible and at least loadable on all keyboards who would embed or shim Leekspinner with it.

- Priorities. Load the resource pack by the following in order of topmost
  1. Next by `.mid` file itself
    - because sometimes, packing everything into just one file makes too heavy on many cheap and legacy keyboards!
    - You can choose to render the `.mid` instructions & `tar.zst` resources separately. Optionally, repack all these file back, into maybe `7z`, `rar`, etc.
    - So you got
    - `miku_senam.mid` which you load for the machine or into Leekspinner which broadcast it into the machine.
    - `miku_senam.tar.zst` next by it, which Leekspinner shim loads.
  2. user `~/.local/share/lib/leekspinner`
  3. system `/usr/share/lib/leekspinner`

## System

### Caching

Recommended to cache file blobs in each & every MIDI file ever loaded.

- `data.LoadBlob` caches extracted data to `~/.cache/Leekspinner`
- Every read of said blob becomes pointer to the extracted cache.
- Making sure subsequent play loads faster, until cache cleared.

### Packing Resources Into Render

It is a best practice to pack everything you see into a single file ala AppImage. 

- Leekspinner spec renders everything into a single `.mid` file
- Splices total usable blobs (audio, orchestration clip, samples, images, videos, etc.) into spliced archives for most compatibility
  - Usually per 50 MB.
  - File named same as the render filename. e.g., if it's `miku_senam.mid`, it'd be
  - `miku_senam_000.tar.zst`, `miku_senam_001.tar.zst`, `miku_senam_002.tar.zst`, so on and so fort.
  - And so in the list, it will look like
    ```txt
    TextCommand://data.loadBlob("miku_senam_000.tar.zst","...");
    TextCommand://data.loadBlob("miku_senam_001.tar.zst","...");
    TextCommand://data.loadBlob("miku_senam_002.tar.zst","...");
    ...
    TextCommand://data.extractBlob("miku_senam_000.tar.zst"); // and start extracting using typical extraction tool like `tar xf miku_senam_000.tar.zst`.
    // And if the archiving standard does not support spliced like 7z, Leekspinner will use conventional batch bus system,
    // Then duplicate above extract command accordingly on the MIDI file.
    ```
- In case different MIDI file shares the same resources, matching checksum will be compared and skipped automatically when matches, otherwise seamlessly overwritten just for this file / session.