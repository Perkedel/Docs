# Random Linux Kernel Panic

## Trigger Panic Manually

- Linux
  ```console
  $ sudo echo 1 > /proc/sys/kernel/sysrq
  $ sudo echo c > /proc/sysrq-trigger
  ```
- FreeBSD
  ```console
  $ sudo sysctl debug.kdb.panic=1
  ```
- Fork Bomb
  - `:(){ :|:& };:`
- Sauce
  - https://unix.stackexchange.com/questions/66197/how-to-cause-kernel-panic-with-a-single-command
  - https://gist.github.com/mittman/6170722
  - http://evan.borgstrom.ca/post/33758728773/forcing-a-linux-kernel-panic

## Moar

- https://superuser.com/questions/1853565/whats-the-proper-way-to-shut-down-after-a-kernel-panic