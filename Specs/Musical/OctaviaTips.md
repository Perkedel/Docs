# ltcgo's Octavia!

How to use Octavia & the MIDI files?

## Try Online Or Download

- Visit one of the following:
  - https://gh.ltgc.cc/octavia/
  - https://blob.ltgc.cc/octavia/
  - https://ds.ygg.ltgc.cc/octavia/ **Yggdrasil yey**. View below section for Yggdrasil network.
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

## Yggdrasil

Setting up Yggdrasil is very simple!

1. Go to https://yggdrasil-network.github.io/
  - & checkout [dacctl's video about it](https://youtu.be/rJt-x-0Jci4)
2. Install Firewall first!
  - e.g., Uncomplicated Firewall
    ```console
    $ paru -Syu ufw
    ```
  - & there are many GUI interfaces about it.
    - KDE has one built-in, in the KDE Settings app.
    - or use `gufw`?
  - Make sure that
    - Defaults are
      - Inbound = `Ignore` / `Deny`
      - Outbound = `Allow`
    <!-- - Necessary Inbound ports are allowed (for future use), e.g.
      - KDEConnect / `1714`. Let's say to connect phone to the PC
      - qBittorent / `6881`
      - syncthing / `22000`. let's say you prepped a sync folder for your media files-->
2. Install now!
3. Enable & Start Service
  - OpenRC
    ```console
    # rc-update add yggdrasil default  # should already be added by the time you install
    ```
  - Simplified init system of certain kind of Distro
    - Content of the script
      ```bash
      #!/bin/bash
      /usr/bin/yggdrasil -useconffile /etc/yggdrasil.conf
      ```
    - Put that into autorun folder somewhere, e.g. in certain distro of that,
      ```console
      $ sudo cp ~/Project/batch/yggdrasil.sh $SERVICE_AUTOSTART_SYSTEM  # assuming it's maybe on `/usr/share/autostart`
      ```
  - Desktop Shortcut service based
    - Content of the shortcut
      ```desktop
      [Desktop Entry]
      Name=Yggdrasil
      Exec=/usr/bin/yggdrasil -useconffile /etc/yggdrasil.conf
      Terminal=false
      ```
    - Put that into autorun folder somewhere, e.g. in certain distro of that,
      ```console
      $ cp ~/Project/batch/yggdrasil.desktop /usr/share/autostart
      ```
  - SystemD
    ```console
    $ systemctl enable --now yggdrasil
    ```
4. Edit configs to finalize the experience
  - **CAUTION**, before you opening up `/etc/yggdrasil.conf`,
    1. your autogenerated config contains **SSL Private Key**, STOP RECORDING NOW!!
    2. Backup first!
      ```console
      $ sudo cp /etc/yggdrasil.conf ~/.Confidential/yggdrasil/yggdrasil_idk.conf
      ```
    3. Export immediately!
      ```console
      $ yggdrasil -useconffile /etc/yggdrasil.conf -exportkey > ~/.Confidential/yggdrasil/yggdrasil_idk.key
      ```
    4. Reinstall new key into system service's accessible directory
      - Because e.g. my SystemD cannot access any user directory
      - let's move it back somewhere belongs to `root`
      - e.g., copy / install the key file seamlessly into an arranged directory somewhere
        ```console
        $ install -Dm655 ~/.Confidential/yggdrasil/yggdrasil_idk.key /usr/share/yggdrasil/.key/yggdrasil_idk.key
        ```
    5. Stop recording & open the text config `/etc/yggdrasil.conf`
      - Using UX-familiar TUI Text IDE, `fresh`,
        ```console
        $ sudo fresh /etc/yggdrasil.conf
        ```
    6. Replace `PrivateKey` line into safer `PrivateKeyPath`
      - delete 🚮
        ```
        PrivateKey: abcf8f8f
        ```
      - replacement 🫴
        ```
        PrivateKeyPath: "/usr/share/yggdrasil/.key/yggdrasil_idk.key"
        ```
    7. Save
    8. Add peers now!
      - List of Peers pls!
        - https://publicpeers.neilalexander.dev/ . [Source Code](https://github.com/yggdrasil-network/public-peers)
      - **PAY ATTENTION**! Once again, on the peer list you were told that,
        - Select peers located **in your country**, then **nearest of your country** (by sea-line oceanic cable topology btw, I think)
          - You can use [Online Submarine Cable Map](https://www.submarinecablemap.com/) to check the cables by your region.
          - So, consider the peers that would be
          - right next to you
          - jumps the shortest length
          - jumps lowest amount of cables
          - Between the jumps, has as many as redundant cables & landings between you & the destination.
        - Pick with the most uptime, at least **100% for over a week** & probably would be more.
        - **Avoid** high latency peer, including, far away peers
        - **Do not add many peers**, you just need few of them! Maybe 2, or 3.
        - Also **no need to duplicate same peer for different protocol**.
      - Look at the `/etc/yggdrsil.conf`, your `Peers` array variable should look like this, e.g.
        ```
        Peers: [
          "tls://ygg.example.io",
          "quic://ygg.example.sg"
        ]
        ```
    7. Save & Close
5. Restart Yggdrasil
  - SystemD
    ```console
    $ systemctl restart
    ```
6. Enjoy!
  - Visit the [Yggdrasil version of the Octavia online](https://ds.ygg.ltgc.cc/octavia/)!
  - Directly visit `https`, not the `http` first, since sometimes the 2secure redirector may not work automatically.

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
- Yggdrasil failed
  - Check the journal!
    - Much easier using [SysD-manager](https://github.com/plrigaux/sysd-manager) from plrigaux!
    - Look up `yggdrasil` & open that service
    - And see tab `journal` of the service view area on the right side.
  - if you found Yggdrasil cannot access exported key (`Permission Denied`)
    - Make sure you really install the key into `root` owned directory, because some init systems cannot access any user-owned directory! I think.
    - Edit the `/etc/yggdrasil.conf` again.
    - This is wrong ❌
      ```
      PrivateKeyPath: "/home/RainbowDash/.Confidential/yggdrasil/yggdrasil_idk.conf"
      ```
    - It should've been ✅
      ```
      PrivateKeyPath: "/usr/share/yggdrasil/.key/yggdrasil_idk.key"
      ```