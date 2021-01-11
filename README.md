# Undetectable_Rootkit

This repo is a revised version from https://h0mbre.github.io/Learn-C-By-Creating-A-Rootkit.

## Hooking Syscalls with Shared Library Injection
* Where
  * `/etc/ld.so.preload`
* What
  * `write()`, `readdir()`, `readdir64()`, `fopen()`, `fopen64()`
* How
  * inject bind_shell and reverse_shell in hooked `write()`
  * hide from `/bin/netstat` in hooked `fopen()`
  * hide from `/bin/ls` in hooked `readdir()`
  

## Potential Upgrades for the Library 
### Suggestion from h0mbre
If you liked this post, and you want to take the library further, I have some ideas on what can be improved:

* Get rid of the syslog trigger, and develop a trigger for the sshd service itself, that way we can get on the box as root without any privesc bread crumbs
* Code up an openssl back connect client/server program so we can get encrypted comms
* Do away with the magic port number hook and instead implement a magic GID which you can set as root on the processes you run
* Extra Bonus: Patch the dynamic linker so that it doesn’t reference /etc/ld.so.preload but silently references a different directory which you have hidden. The dynamic linker should still report that it checks /etc/ld.so.preload but we will know better :)
