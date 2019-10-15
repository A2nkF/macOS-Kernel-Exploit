# macOS-Kernel-Exploit

## DISCLAIMER
You need to know the KASLR slide to use the exploit. Also SMAP needs to be disabled which means that it's not exploitable on Macs after 2015. These limitations make the exploit pretty much unusable for in-the-wild exploitation but still helpful for
security researchers in a controlled lab environment.

This exploit is intended for security research purposes only.

## General
macOS Kernel Exploit for CVE-2019-8781 ~~(currently a 0day. 
I'll add the CVE# once it is published ;) )~~. 

Thanks to @LinusHenze for this cool bug and his support ;P.

## Writeup

Probably coming soon.
If you want to try and exploit it yourself, here are a few things to get you started:

- VM: Download the macOS installer from the appstore and drag the `.app` file into VMWare's `NEW VM` window
- Kernel Debugging setup: http://ddeville.me/2015/08/using-the-vmware-fusion-gdb-stub-for-kernel-debugging-with-lldb
- Have a look at the _kernel_trap function


## Build

I recommend setting the bootargs to: `debug=0x44 kcsuffix=development -v `

:warning: **Note**: SMAP needs to be disabled on macs after 2015 (`-pmap_smap_disable`)

You will need XCODE <= 9.4.1 to build the exploit. (It needs to be 32bit)
Downloading Xcode 9.4.1 Commandline Tools should be enough ;)
Download: https://developer.apple.com/download/more/

```
make
```

## Execution

```
./exploit <KASLR slide>
```

Tested on macOS Mojave: `Darwin Kernel-Mac.local 18.7.0 Darwin Kernel Version 18.7.0: Thu Jun 20 18:42:21 PDT 2019; root:xnu-4903.270.47~4/DEVELOPMENT_X86_64 x86_64`

**Demo**:

[![asciicast](https://asciinema.org/a/gtOLsNfxPSwcOOYKUwcH0JFJd.png)](https://asciinema.org/a/gtOLsNfxPSwcOOYKUwcH0JFJd)
