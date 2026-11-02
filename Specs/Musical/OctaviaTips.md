# ltcgo's Octavia!

How to use Octavia & the MIDI files?

## Try Online Or Download

- Visit one of the following:
  - https://gh.ltgc.cc/octavia/
  - https://blob.ltgc.cc/octavia/
- View Source Code & Back them up now!
  - https://codeberg.org/ltgc/octavia/
  - https://github.com/ltgcgo/octavia
  - Also the important stuffs
    - https://codeberg.org/ltgc/midi-db OR https://github.com/ltgcgo/midi-db . MIDI definition database
    - https://github.com/ltgcgo/midi-data . Community yoinked MIDI demo files from various brands, & individual artist songs
- Locally Download (**TEMPORARY**, MAY BROKE, PLS WAIT UPSTREAM BUILD DOC!)
  - Prerequisite!
    - `deno`. It should already exist everywhere on your beloved Linux Distro package manager.
    - `git`. Duh!, how would we ever version control & download cool stuffs elegantly without it? 
  - Go to a proper project playground space then clone / download all three
    ```console
    $ cd Project  # Go to XDG Project file from your home
    $ mkdir -p OtherMIDIProject/ltgcgo && cd OtherMIDIProject/ltcgo  # make the proper playground space for those packages & go there

    # Now clone!
    $ git clone --recursive https://codeberg.org/ltgc/octavia.git
    $ git clone --recursive https://codeberg.org/ltgc/midi-db.git
    $ git clone --recursive https://github.com/ltgcgo/midi-data  # WATCH OUT! the MIDI files & the rendered sample audio are only on GitHub, because dumping it also on Codeberg is bad idea atm, HUUUUUGE!!!
    ```
  - Make note that these repositories are designed to be deployed on a static web server and seamlessly aligned one to another.
    - Every packages will be deployed a line towards selected domains (`gh.ltgc.cc`, `blob.ltgc.cc`, etc.)
    - All these projects are built as the static web pages, because that's how a simple Page deploy works, apparently.
      - Unless you're doing Server Side Rendering which is for whole another video.
    - Each will be assigned root folder name after the domain, so we got:
      - `localhost:8010/octavia` just like `gh.ltgc.cc/octavia`
      - `localhost:8010/midi-data` just like `gh.ltgc.cc/octavia`
      - `localhost:8010/midi-db` just like `gh.ltgc.cc/midi-db`
    - But we are not those static servers like GitHub Pages.
    - Don't worry, let's just manually clone the rest of the packages, **which you should already have done above**.
    - Keep note the `midi-db` & `midi-data` for later steps
  - Build!
    - Go to `octavia` project
    - Start building just like how would the GitHub Action do.
      ```console
      $ ./shx generate  # to generate data for Octavia
      $ ./shx build  # to compile now
      $ ./shx babel  # to build the repack the compile for Windows XP compatible
      $ ./shx sitemap  # to build simple sitemap
      $ ./shx srcMap  # to link available source maps
      ```
    - Repeat the step for `midi-db` as well. You'll just need to
      ```console
      $ ./shx build  # to compile all available data for the MIDI definition database
      ```
  - Symlink `midi-data` & `midi-db` into the `octavia` deployment!
    - Easier with KDE Plasma
      - in `octavia/dist`, `+ Create New` `Symbolic Link to File or Directory...`
      - Name the respective symlink as follows
      - `midi-db` 👉 the `midi-db` back next by Octavia project folder
      - `midi-data` 👉 the `midi-data` back next by Octavia project folder
    - Classic Terminal
      - Create `-s` (Symbolic) link now! args are the target folder path there, and then what the name of your symlink here.
        ```console
        $ ln -s ../../midi-db midi-db
        $ ln -s ../../midi-data midi-data
        ```
  - Run Server Now!
    - Go back to `octavia`
    - Serve now!
      ```console
      $ ./shx web
      ```
    - Note the port number. Usually it would be `8010`
  - Open the localhost now!
    - Visit `localhost:8010`, assuming indeed your `deno serve` points to the port number there.
    - and go inside `octavia` so you should ended up in `localhost:8010/octavia` just like Pages deploy would be.
  - Enjoy!
  - Terminate
    - on the Terminal you ran `./shx web` on, Signal Interrupt by `Ctrl` + `C` to terminate the server.
  - Update!
    - Go to respective repositories that just got new commits
    - Pull / download the update now!
      ```console
      $ git pull
      ```
    - If it failed, make sure the repositories are cleaned up.
      - Assuming that you did not edit anything, you can try resetting everything
        - **Back up all your edits first!**
        - Stash stray files
          - GitHub Desktop offers the GUI option to stash those files after pull failures.
        - hard reset to restore delete everything back to originally cloned
          ```console
          $ git reset --hard
          ```
    - Rebuild everything that just got changed & pulled into the new commit! Remember, for each of those updated repos,
      ```console
      $ ./shx build
      ```
          

## Keybind

- Cambiare
  - `Display Fullscreen` (Keyboard `Enter`). Full screen the Cambiare display, hiding above controls & scroll bar
- Fake MIDI Module Display
  - `PART ◀️▶️` (Mouse Scroll / Click Horizontal Edges). Move between MIDI channels
    - Extra port channels (`B` and more) unlocks when you loaded MIDI file that involved over 16 Channels
  - `SCREEN ◀️▶️` (Keyboard `Shift` + Mouse Wheel / Click Vertical Edges). Move between display tabs if available
    - Fake QY. Move between different parameter screens
      - Song
      - Normal
      - Mixer
      - Send
    - Fake PSR.
      - Only Vertical Edges clicking works, no `Shift` + Scroll.
      - Top edge switches between `SONG`, `STYLE` view & `VOICE` view buttons.
        - Octavia `STYLE` does not do Rhythm mode unlike actual Yamaha Keyboards, only viewing like `VOICE` view.
        - Like when on cheap Yamaha Keyboards you got either `SONG` / `STYLE` + `VOICE` buttons lit, Octavia only has `SONG`, `SONG` + `STYLE` lit & `SONG` + `VOICE` lit.
      - Bottom edge switches number segment view between `TEMPO` & `MEASURE`.

## Troubleshooting

- Online deployment's Cloudflare and other scrape protection kept falsely blocking me!
  - The protection thought you're one of those illicit scraper bots.
  - This is because you probably have
    - Opened so many tabs & groups
  - Try to
    - Hibernate those tabs
    - Update to latest & greatest browser that should do those enlightening for you
    - Transfer all tabs & businesses from Thorium & stop using it anymore. You have to go to latest & greatest Chromium
  - If all else still failed, download locally.
    - You can also tell the author privately through Telegram. Sorry, idk where, go to DTM-Hub.