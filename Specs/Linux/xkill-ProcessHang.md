# `xkill`

Window hang? use `xkill`.

- How to launch `xkill`
  - Spotlight Method
    - `Alt` + `Space` to open Spotlight / Search Launcher
    - type `xkill`
    - execute
  - Keyboard shortcut
    - Some distro, PC Builder, or Ricer may assign macro to launch `xkill` from factory / workshop.
    - Usually, this might be `Shift` + `Ctrl` + `Alt` + `X`.
    - Overall, **this shortcut by default typically do not exist by default** from any desktop environments I could find.
  - Terminal
    - run command `xkill`
- Using `xkill`
  - Kill window
    - With xkill active, your mouse cursor turns to `X` or `☠️`. This indicates kill process mode, the xkill is active.
    - click a window to destroy.
    - Done. The window closes, and its process will also terminate.
  - Canceling
    - ~~Cancel by pressing `ESC`~~ 
    - Ctrl+C in the terminal where you ran `xkill` at.
    - press any other key that is not Left Mouse Button?
  - Disclaimer
    - `xkill` only terminates X connection off the process.
    - It is not Kill Process. However, the process can exit itself if their last window is destroyed.
- Sauce
  - https://www.geeksforgeeks.org/linux-unix/how-to-kill-processes-on-the-linux-desktop-with-xkill/
  - https://askubuntu.com/questions/1081524/what-does-xkill-mean-and-do
  - https://en.wikipedia.org/wiki/Xkill