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

> [!CAUTION]  
> Please do not scam people by only packing *MP3 music* onto the file.
> We expect you to meticulously make full MIDI cover, where Audio used only for voices.

Audio Synchronized play! Play whole Audio file

```txt
TextCommand://data.loadBlob("sing_tape_waifu.opus.zst", "8347298742987ufahsfhasdkjhf"); // Load the sound source

TextCommand://audio.play("sing_tape_waifu.opus.zst", 0); // At certain timestamp, play it now from the file beginning zero second!
```

- Different than Yamaha MU's implementation!
  - Won't occupy Font of the Synth at all.
  - Plays in a separate Media Player module, strictly synchronized & clocked to the MIDI Player.

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

- Works like MU
  - Occupies as Letters to the Synth.
  - Note this plays `AAaa`
  - and another `Baaa` like that.

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

### Insert this Plugin Setup!

You can load Plugin Setup of a MIDI channel before going out to the Output.

```txt
TextCommand://data.loabBlob("vst_setup.lgr.zst","..."); // Load your plugin graph!

TextCommand://midi.insertPlugin("vst_setup.lgr",0); // And insert that to Ch. 1
```

### Manually EFX

Or you can manually build your Effect

```txt
TextCommand://data.loadBlob("efx_distort.json.zst",".."); // load plugin config!

TextCommand://midi.setEffect("suara_serak.clap",0,"efx_distort"); // and load built-in distortion with the setting!
TextCommand://midi.setEffectParam("drive",177); // and make further adjustment to the distortion plugin parameter, based on available in the parameter slider interface.
TextCommand://midi.enableEffect(0, false); // Turn off temporarily
TextCommand://midi.enableEffect(1, true); // and back on again.
TextCommand://midi.clearEffect(); // And clear it once you're done.
```

- Ultra better than anything!
  - EFX adds per channel.
  - Same setup can be duplicated to another channel.
  - Can connect same setup to chanel from channel
  - Of course, unlike others, all channels can have completely different setups
  - Unlimited! Per channel can have too many setup as long as the keyboard can handle those many instances
  - Because the Synth have Plugin Host. Inside, bunch of audio patch cables you can sever to be replaced with said EFX's.
    - Start is the Font
    - End is Audio out
    - In the middle is where your plugin area is.
    - It also has MIDI event jacks too, in case a Plugin depends on Note press & other parameters.

## Experimental & Funny

### MIDI file in MIDI file

You can pack another MIDI file in MIDI file too!!, even engage download of other files too!

> [!CAUTION]  
> - use TextCommand `data.downloadBlob(sauceURL:String)` sparingly
> - External download will lag the whole player & can desync your whole Orchestra
> - **Avoid scamming people using downloader / ala-Torrenting trick like this!**
> - the Download Blob shall only / exclusively be used for resources that you also made yourself.
> - If you had to share download link of somebody else's MIDI files, **you must fully sparsdat them**, i.e. `loadBlob` the all whole MIDI files instead. 

```txt
TextCommand://data.loadBlob("yo_dawg.mid.zst", "..."); // Load your MIDI file
TextCommand://data.downloadBlob("https://example.com/midis/yo_dawg.mid"); // Engage Aria2 (falls back to wget) to download MIDI from a website or network storage

// and execute the Orchestration command in the timestamp you desire
TextCommand://midi.play("yo_dawg.mid", "megurine_luka_usb"); // Orchestration: Play this file on another device e.g. a digital piano / clavinova
TextCommand://midi.play("yo_dawg.mid"); // Or here, at another free empty MIDI slot after this MIDI slot round robin.
// E.g., is this MIDI file itself plays at `A` (from Ch. 1), then above command goes to `B` (from Ch. 17).
```

### Orchestration

You can set up a mega-orchestra consisting multiple MIDI modules, where your Leekspinner MIDI player acts as the maestro

```txt
TextCommand://data.loadBlob("for_rolandSC8850.mid.zst", "..."); // Load sheet music for SC-8850
TextCommand://data.loadBlob("for_YamahaGenos2.mid.zst", "..."); // and another for the other, Yamaha Genos 2.
TextCommand://data.loadBlob("for_HatsuneMiku.mid.zst", "..."); // finally, for this player itself

// And then play them all!
TextCommand://midi.transfer(3); Move this playback of the master MIDI file to slot `D` (Ch. 49).
TextCommand://midi.play("for_rolandSC8850.mid", "88emu_0"); // play for the SC-8850. Won't occupy any slot here
TextCommand://midi.play("for_YamahaGenos2.mid", "Yamaha USB"); // and Genos 2. Still won't occupy any slot here..
TextCommand://midi.play("for_HatsuneMiku.mid", 0, 0); // And to this itself (first `0`), at slot `A` (Ch. 1, second `0`). Occupies Slot Ch. 1-16 now here.
```

- MIDI played will engage resets, other SysEx, and other data only to each respective target. 
  - Roland's MIDI file only had `GM1` then `GS`, but the rest won't get contaminated
  - Therefore Yamaha Genos won't hear `GS`, but just `GM1` then `XG` reset from their MIDI file.
  - Same goes to itself. The Leekspinner keyboard won't hear `GM1`, `GS`, nor `XG` at all, and only hear `GM2` followed by `LS` from this MIDI file just for `D`, and then another just for `A`.
- Note, many MIDI files will have initialization Bar, **so provide some dedicated bars** for the master MIDI file for every slave MIDI files!
  - If these slave MIDI files first init goes for 1 bar maximum, then give the master 1 empty bar, before actually putting the orchestra notes, SysEx's, & more data.
- Leekspinner keyboard's MIDI player is *containerized* & modular off of the synth parts of it, which makes this separation possible
  - So that Leekspinner has
    - MIDI Player. Load file and broadcast MIDI data
    - Style Player. Load Style file, which is a special looped MIDI file that works like finite state machine.
      - This is how Yamaha PSR demo was orchestrated btw! Master MIDI file has the play, and it controls the style player.
    - Media Player. Specially Riced MPV (VLC Fallback) to play audio & video blob coming from MIDI file & transmission.
    - SFe synth. SoundFont-e loader
    - FolderWave synth. Default synth of Leekspinner
    - Plugin Host. Load plugins, FX & Instrument, CLAP, VST3, etc.
    - Pipewire. Core sound driver & graphical connection system ala-JACK
    - Runtime loading support: Native Linux, WINE, etc. run some apps, lessons, & games
    - built-in Keyboard. Emulates Concert Grand feeling with Input feedback for LEDs, haptic, & other ASMR.
  - Leekspinner & implementations are expected to be built modular like this. Apps to play MIDI, and another to load SFe, GUI Desktop Environment for control, etc. are separated.

### Heart Organ As A Clock

> [!NOTE]
> Make sense in Performance use case only.

You have a new External Clock system: Heartbeat from your own organ

```txt
// send the following Command into your LeekSpinner, or use setting menu.
TextCommand://midi.changeClock(1, "wristwatch", CLOCK_INTERPOLATION_HEARTBEAT); // Set clock to External (`1`), Source `wristwatch`, Interpolation of `heartbeat`.
```

- Heartbeat BPM (the MIDI player analyzed from IN) = playback Tempo
- Playback now ignores all Tempo Change messages

#### Every Heartbeat Advances

For funnier outcome, you can remove interpolation & MIDI playback advances strictly per heartbeat.

```txt
TextCommand://midi.changeClock(1, "wristwatch", CLOCK_INTERPOLATION_DEFAULT); // same device, but now interpolation set to default or `tick` / `CLOCK_INTERPOLATION_TICK`
```

- MIDI playback step now advances only every `Lub` / Systole of your heart.
- Still ignores all Tempo changes
- Another good case of Orchestra, you can build the master MIDI file so e.g. it randomizes some parameters every Systole, and affects all connected slave MIDI modules.
  - Every step of message is different value of it
- Use Loop to make MIDI player cycles back to the last Loop Start.

### Alternative Clocking

Let's say you're unable to ensure any means of `MIDI Ext Clock` tick message, you can set the clock source from somewhere else, e.g. Note type A & type B.

> [!IMPORTANT]  
> - MIDI Player will not heed by clock commands from files by default. At this point, you can only do so direct from MIDI IN
> - If you wish for MIDI player to heed all messages masochisticly even from files, you can go to setting and enable said options.
> - You cannot have separate clocking in 1 MIDI player app. Consider re-instancing another MIDI player locally or externally if you wish to have a desynced / polyrhythm tempo setup.

```txt
TextCommand://midi.changeClock(1,0,CLOCK_INTERPOLATION_DEFAULT,CLOCK_SOURCE_NOTE); // External again, but use built-in keyboard, 
TextCommand://midi.addClock(CLOCK_ADDSOURCE_NOTE,"3C"); // and Middle C is the clock. Maybe to Systole
TextCommand://midi.addClock(CLOCK_ADDSOURCE_NOTE,"3D"); // as well as D next by. Also for Diastole, e.g.

TextCommand://midi.clearClockSource(); // Once done, clear them!
TextCommand://midi.resetClock(); // and reset clock back to default.
```

### Orchestration 2: Auto-hotkey

You can also make the `.mid` file an `.ahk`-like script. Because `.mid` file are sequenced & timestamped, this is a perfect niche use case for stuffs that needs to be done in a specific timestamp rather than instantaneous per-line.

> [!IMPORTANT]
> - For safety, MIDI Player ignores all AHK & CMD commands by default.
> - Always review the MIDI file before letting the AHK and/or CMD enabled with it.
> - MIDI Player will always warn you before you can play, if a MIDI file contains AHK or CMD TextCommand'd text messages & offers you to review what are those.

```txt
TextCommand://ahk.setMousePct(20,20); // Put cursor x 20% & y 20% from left and top of screen.
TextCommand://ahk.mouseClick(0); // left click!

TextCommand://cmd.bashExec("test.sh");// Or basically run terminal batch script, you can too!
TextCommand://cmd.bashInterp("chmod +x install.sh"); // Or even directly have a string of shell script, yess! 
// Supports only UNIX-like bash, no PowerShell nor CP-M-like tho.
TextCommand://cmd.pyExec("test.py"); // Let's put Python as one of the nepo baby supported!
```

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

> [!TIP]  
> `loadBlob` shall automatically extract the archive immediately by default.  
> e.g., the load blob `mydata.txt.zst` will be usable as `lcd.cat("mydata.txt", PRINT_HEADER_TITLE)` **without the `.zst` extension needed anymore**.

## Safety

### Scam MIDI file

If the Download link MIDI file only got Audio, you'll be offered to convert the file to actual data inside

```console
Scam MIDI file detected! Convert file now?
- Extract all the data out to each files, decompressed.
- Downloaded MIDI file will be moved to Trash.
Confirm (Y / N):
```

- Can also detect deliberately spliced audio files
  ```console
  Scam MIDI file detected!: Spliced Audio files, Convert file now?
  - Extract & merge recordings into proper file
  - Track cut-off detection per silence
  - Downloaded MIDI file will be moved to Trash.
  Confirm (Y / N):
  ```
- And even deliberately through Soundfont press notes
  - `: Press Note Audio Samples, Convert file now?`
  - May cause false alarm, especially song made in Spliced Tape style. Like recording something to DAW only with Audio & composed it like using Audacity.
  - Review the MIDI file carefully! Avoid accusing or pre-banning the author!