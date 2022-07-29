
NetBSD SIMH HOW-TO

This guide is intended to help you install NetBSD on the SIMH VAX emulator.

    Install SIMH. This document assumes you are using the simh package from pkgsrc, which installs the binary as simh-vax and the VAX CPU firmware into /usr/pkg/share/simh/
    Download a NetBSD/vax CD ISO image.
    Create a file, say netbsd-boot containing the following:

            load -r /usr/pkg/share/simh/ka655x.bin
            set cpu 64m
            set rq0 ra92
            at rq0 netbsd.dsk
            set rq1 cdrom
            at rq1 /path/to/vaxcd.iso
            at xq0 name-of-network-interface-on-host
            boot cpu

    This will configure a emulated MicroVAX 3900 with an RA92 disk (/dev/ra0*), and the CD image as an RRD42 CD-Rom (/dev/racd0* or /dev/ra1*). See the SIMH documentation for other options
    Start the emulator program

            /usr/pkg/bin/simh-vax netbsd-boot

    At the VMB prompt, boot from the CD by typing:

            boot dua1:

    Proceed with the NetBSD install. You may want to not install the X11 stuff, since SIMH doesn't emulate a frame buffer. For versions of NetBSD before 6.0 you will need to change the CD drive from /dev/cd0a to /dev/ra1a when prompted. (NetBSD 6.0 and later should pickup the correct /dev/racd0a automatically)
    After a considerable amount of time, the installation finishes, and you may shut down or reboot
    You can now type q at the emulator prompt to exit the emulator
    You can remove the "set rq1 cdrom" and "at rq1 /path/to/vaxcd.iso" lines from netbsd-boot as you no longer need the install CD image. Alternatively you can leave them in case you ever want to re-install
    Restart the emulator like so:

            /usr/pkg/bin/simh-vax netbsd-boot

    At the VMB prompt, boot from the installed disk by typing:

            boot dua0:

    Welcome to NetBSD!

If you are interested in helping this document cover other NetBSD ports, or have any other comments or suggestions, please contact Lars Brinkhoff <lars.spam@nocrew.org>, or the NetBSD WWW group.
Acknowledgements

The initial version of this HOW-TO was written by Lars Brinkhoff. Some of the information in this page was derived from an email sent by Mirian Crzig Lennox .
	NetBSD Home Page
	
	NetBSD Documentation top level
(Contact us) $NetBSD: emulator-howto.html,v 1.6 2012/07/17 06:51:19 abs Exp $
Copyright © 2002-2003 The NetBSD Foundation, Inc. ALL RIGHTS RESERVED.

