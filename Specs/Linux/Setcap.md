# Setcap

Linux and many other UNIX & alike distros caps network port numbers on unprivileged user. I.e., **you cannot simply port 80 without root** being who's running it.

Let's use `setcap` to change that.

> [!CAUTION]  
> Lab Experimental use only!  
> Recklessly opening port to applications for unprivileged users may cause vulnerability!
> 
> Alternatively, try to use another root-level daemon service that can redirect ports seamlessly for your software.  
> With this, set your server app to higher port numbers and configure the daemon to bridge those numbers right to your target port numbers.

## Simply Open Port

e.g., I have a server app written in python. I want this `py` server app able to open port `80`, `443` and whatever under the privileged number it is.  
You will **allow the python runtime itself** to have that port for unprivileged user.

```console
$ sudo setcap 'cap_net_bind_service=+eip' /usr/bin/python3.14
```

- `cap_net_bind_service` is variable to configure port number binding of that software.
- Operators
  - `=`
  - `-` remove the..
  - `+` add the..
- And the flags are (see [`cap_from_text` manpage](https://linux.die.net/man/3/cap_from_text))
  - `e` effective
  - `i` inheritable
  - `p` permitted
  - **Case Sensitive**
- **You must target the app file itself**, cannot through symlink or any shortcuts, because the script will eventually check the OG file itself.
  - Traverse your runtime app recursively until it leads you to the original file, e.g. using `ls` the file that turns out to be a symlink.
- [Sauce](https://superuser.com/a/892391/1036816)

## Removal

I know this is a bad idea! And thankfully found a better lightweight daemon that can bridge my port numbers better.  
You can clear the privilege (& other capabilities too) of the app runtime now

```console
$ sudo setcap -r /usr/bin/python3.14
```