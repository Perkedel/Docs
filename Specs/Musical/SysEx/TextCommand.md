# LeekSpinner TextCommand

`TextCommand://` is a special Text / Marker syntax that will be recognized by our LeekSpinner MIDI machine, when such message that started with `TextCommand://` has been received.

TextCommand exist to exploit fault in MIDI standard, where slotting in Hardware Manufacturer ID into the standard would cost very exorbitant. TextCommand will be the Gratis, Open Source, & FULL VERSION solution for all manufacturers building custom commands for their MIDI module

## How to TextCommand

it's easy! Simply send Text / Marker message starting with `TextCommand://` and add your commands there.

```txt
TextCommand://print("hello world")
```

The command that follows would be composed C-like, Lua-like.

### If Else Statements

All If-else statement must be immediately closed in that message, to be considered valid

```txt
TextCommand://if(a=1){print("a is true (" + 1 + ")");} // YES

TextCommand://if(b=1)print("b is true (" + 1 + ")") // YES

TextCommand://if(a=1){
TextCommand://print("a is true (" + 1 + ")")
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

Terminator `;` is optional, if a TextCommand goes for just 1 command. Otherwise, you have to have `;`.  
That includes commands inside `{}` bracketed function container.

```txt
TextCommand://print("hello world") // YES

TextCommand://print("hello world"); // YES, again, the `;` is optional if that's the only command in this message.

TextCommand://{print("hello world");} // YES, the `;` must be there, or else ERROR!
```

### Library

You can do import libraries ala Nim-Lua!

```txt
TextCommand://local Vocaloid = import("Vocaloid.lsl"); // import! This variable now becomes the class instance of it

TextCommand://Vocaloid.set_voicebank("miku_classic"); // and do some functions there!, such as call a function for this channel.
TextCommand://Vocaloid.bind_plg(0); // install to virtual slot!
TextCommand://midi.set_mapping("plg_0"); // set voice map to Vocaloid Plugin now!
```