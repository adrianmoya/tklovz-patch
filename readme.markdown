TKLOVZ
======

This patch will prepare a turnkeylinux lucid filesystem to work as an ovz template. It only handles the convertion of the filesystem, so the recomended way of using it is through the TurnkeyLinux Development Environment, using the main tkliso2ovz script. For more information, ask in the [TurnkeyLinux Forums](http://www.turnkeylinux.org/forum)

You must note that when using openVZ templates:

- Confconsole won't be running when you access to the console of the container. You must run confconsole if you need access to it. 

- When using venet, confconsole won't work as intented, because you are managing the ip configuration at another level. If you wish yo use confcosole to work as usual, use veth as your network type. Be sure to check the [openvz docs](http://wiki.openvz.org/Differences_between_venet_and_veth) about the differences 

- The template name will be the iso name plus -ovz.tar.gz at the end. So if your going to use it in proxmox, be sure to rename it following their guidelines:

<lt;OS>gt;-<lt;OSVERSION>gt;-<lt;NAME>gt;_<lt;VERSION>gt;_<lt;ARCH>gt;.tar.gz
For Example: "turnkeylinux-10.04-revision-control_11.0_i386.tar.gz"

- The host name ends up being renamed to what you specify in the creation of the container. Also the root password is specified in the creation step.

- Inithooks don't get runned. So you must manually execute the command /usr/lib/inithooks/run to complete your appliance setup.

If you have any further question, email me at adrian at turnkeylinux dot org

Many thanks to Jeremy Davis (jedmeister) as he had the main idea and did the initial work of leveraging tklpatch for ovz conversion. 
