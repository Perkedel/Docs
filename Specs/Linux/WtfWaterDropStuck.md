# WTF, stuck on Waterdrop

Bruh, my canberra broke?

- https://bbs.archlinux.org/viewtopic.php?id=281490
  - Disable Legacy X11 bell now in your Pipewire!!
  - Put this into `/etc/pipewire/pipewire.conf.d/disable-bell.conf`
    ```conf
    # No Legacy Bell allowed
    # https://bbs.archlinux.org/viewtopic.php?id=281490
    context.properties = {
        module.x11.bell = false
    }
    ```
  - Restart Pipewire.
    - Probably best idea to restart whole system, since your Pipewire is the main Audio system.
  - See doc
    - https://docs.pipewire.org/page_man_pipewire_conf_5.html