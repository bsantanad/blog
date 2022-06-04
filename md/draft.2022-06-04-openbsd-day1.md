# switching to openbsd for workstation - day 1


### this goes in a box
If you want to skip the whole story thing, at the bottom there is a section on
all the problems I had, and some troubleshooting. So you can go ahead and see
if any of that helps
### this goes in a box

From a while now, I was tinkering with the idea of switching my workstation to
a non-systemd distro there are a couple of reasons, if you are interested in
why some people don't like systemd you can read this really [cool
article][systemd] that talks about it. Then that idea was to ditch linux all
together and install a BSD system in my computer.

Anyway, the only thing stopping me from changing from a popular distro
(fedora) and linux for that matter. Was the compatibility issues, I was still
in college and my professor might ask us to install something that only works
in the popular distros, or even worse on Windows. But I'm out of college now,
so I don't have that problem anymore.

Then it began the question, FreeBSD or OpenBSD, I was leaning toward the first
one because it has more software compatibility, but then I realized that most
of the things I use my computer for are just programming in the terminal, and
browsing the internet.

Since I like OpenBSD philosophy better, I decided to give it a try, and see if
I can use it as my daily workstation.

This is the story of my first day. I'll include the mistakes I made for future
reference.

With that being said, take into consideration that I'm not a UNIX master or
anything like that, so the mistakes I made you may consider silly or things
that happened for not reading the docs.

## installation process

So, once I downloaded openbsd from the website and flash it into an usb. I
thought: "will I need something from my current workstation?", I tar everything
I think I needed backed it up and booted the laptop form the usb. The only
"issue" I had was that when selecting the disk where to install the OS I did
not saw any disks in my laptop, I just saw the usb I was booting from. After a
little bit of googling I figured it was because I needed to go to the BIOS
menu, and change the disk from using RAID to AHCI. After that, both of the
disks showed up.

Then I continued thru the installation options and all that, until I saw the
successful install message, rebooted the machine, and was ready to start
customizing the os. 

When suddenly it did not boot into and OS, actually it did not boot into
anything. This took me an awkwardly amount of time to figure out. So let me
start by saying that I'm not familiar with how partitions works and all that
most of the time I let the installer do his thing and continue with my life.

This time, I saw the partition table and thought it was okay so I continued
with the installation process. Nevertheless I did not realize I was using
MBR instead of GPT. That is why my machine was not identifying the boot partition
after changing the configuration to GPT it all worked fine. (this is the part
where you roll your eyes and say, "that is the worst explanation I've heard,
this kid should learn more about disks, file-systems and all that" but anyway
lets continue)


# troubleshooting

- do not see any disks in the installation process? go ahead and change the
  BIOS setting of the disks from RAID to AHCI



[systemd]:
https://unixsheikh.com/articles/the-real-motivation-behind-systemd.html 


