## What is this?

A very very stupid fake sudo,using polkit `pkexec` to grant permissions.It can partly replace sudo in most common scenarios.

## Why this is created

Both sudo and polkit are able to grant permissions to process,and sadly they  are both volunrable,and installing both is equivalent to doubling the probability of security problems.As we can see, many CVEs of Linux desktop are related to both of them.Meanwhile,having two tools with the same functions on one computer sounds not satisfying.Polkit has better intergration with desktop environments(in particular,gnome) and allows a finer control of centralized system policy.But there are still some scripts depending on sudo.So it's a good idea to write some wrappers to make polkit have sudo functionalities,just like xwayland and pipewire-pulse.

## Installation guide

On Arch Linux you can simply get it from AUR,like :

```bash
yay -S polkit-fakesudo
```

By the way,yay and paru can both use this sudo as real one:)

If you are using other distributions,you can manually place `sudo` in `/usr/bin/` ,`implement.sh` in `/usr/lib/polkit-fakesudo` and `help1` and `help2` in `/usr/share/polkit-fakesudo` , but you'd better do it with your package manager.

Remember that in some cases this fake sudo cannot fully simulate the behavior of real sudo (which means,when you run some apps depending on sudo ,they may run into problems)and may contain severe bugs that hasn't been found!

You are also advised to check which packages depend on sudo with your package manager (maybe also try to figure out why and how).

## How to contribute

Just send PR to this repo.Any kind of contribution is welcomed.If you can write a better implementation with Polkit's ABI and reproduce sudo's ABI,I'm sure that the whole community will be greatly thankful to you!Maybe you can write in rust to get us more excited.
