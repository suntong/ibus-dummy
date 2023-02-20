# ibus-dummy

Dummy `ibus` package for KDE and XFCE (Kubuntu and Xubuntu) to fix Zoom Debian package's dependency.

Brought you by DM yours truly, and available directly by `apt install` from his [ppa repo](https://cloudsmith.io/~suntong/repos/repo/packages/), which has 115 Packages and 44486 Downloads as of Sunday, February 19, 2023.

> ![image](https://user-images.githubusercontent.com/422244/220007585-d7ac987f-ee8f-4787-9506-f1151ca4d303.png)

## Usage

### Repo info

- [Packages available for Linux distros](https://cloudsmith.io/~suntong/repos/repo/packages/) are
  * [Debian](https://cloudsmith.io/~suntong/repos/repo/setup/#formats-deb)

The repo setup instruction url has been given above.
For example, for [Debian](https://cloudsmith.io/~suntong/repos/repo/setup/#formats-deb) --

### Debian repo setup & package installation


```sh
curl -1sLf \
  'https://dl.cloudsmith.io/public/suntong/repo/setup.deb.sh' \
  | sudo -E bash

# That's it. You then can do your normal operations, like

sudo apt update
apt-cache policy ibus-dummy

sudo apt install -y ibus-dummy
```

This will provide a dummy/fake `ibus` package for whatever tools that insist needing it.

If somehow you need the real `ibus` package, then just uninstall this one and install `ibus` instead.


## Why the hell?

I have both ibus and fcitx installed in my KUbuntu, which is a bad idea. 
The reason for that is because of the `zoom` that I need to use, and from these two pages, I can see that such requirement is really unnecessary:

1. [Annoying ibus dependency in zoom .deb files](https://devforum.zoom.us/t/annoying-ibus-dependency-in-zoom-deb-files/67293)
1. [Zoom Debian Linux package requires ibus even on KDE and XFCE](https://community.zoom.com/t5/Meetings/Zoom-Debian-Linux-package-requires-ibus-even-on-KDE-and-XFCE/m-p/62247)

Here are a few quotes:

> - The .deb files for downloading zoom come with ibus in the “Depends:” field. That’s a problem for many Debian/Ubuntu users, and I’ll try to explain why.
> - Needless to say I’m very disappointed at Zoom’s way to respond to my request so far.
> - I’m working with the maintenance of a tool (im-config) used in Debian and Ubuntu to facilitate the configuration of input methods, e.g. IBus. It’s in that role I have received complaints about the ibus dependency in the Zoom .deb file, and it’s in that role I’m here.
> - This is osamu@debian.org (my official Debian contact address) who is a core member of maintaining ibus package for Debian. (Gunnar is another core member too. He is heavily involved in Ubuntu side.)
> - His request is not a mere “user request”. This should be considered a demand by the GNU/Linux distributions to ZOOM.
> - If Zoom provide package for Debian/Ubuntu (deb-packages) with technically sound contents, ZOOM should listen to us.
> - Any updates on this? Just installed zoom and got this too. This dependency is annoying and worthless
> - This excuse for “remote control on a remote machine” is pathetically lacking understanding how “Depends:” field should be used for Debian package. This should be used only for packages which is required under all installation environment. Doing this for a particular environment is considered rude engineering. 
> - I’m a Debian Developer and hence familiar with the conventions and requirements for Debian packages, aka “.deb” files. As currently defined, the way that the Zoom Debian packages use relationship fields (such as Depends:) violate the Debian packaging policy, outlined here: 7. Declaring relationships between packages — Debian Policy Manual v4.6.1.1

However all the requests fall into deaf ears and 1 month later, _"This topic was automatically closed 30 days after the last reply. New replies are no longer allowed."_ and that results comments from link 2:

> - The Zoom Debian Linux package is requiring ibus. But ibus is part of GNOME desktop. So installing zoom_amd64.deb under KDE Plasma breaks keyboard support due to ibus and related dependencies which do not work under KDE.
> - Yep, I am doing a new install of Zoom and suddenly get dependencies on ibus, libegl1-mesa, libxcb, python3-ibus, ibus-gtk and a few others. I am  using a few month old Linux distro so there should be NO reason Zoom won't install. I don't need ibus, it will ruin my setup. This is just crazy. . . When a multi-billion dollar goliath like Zoom hires sub-par developers to package their software, arguably the most important job in a software firm - they deserve to fail! I read the Support forums on this same topic and the absolute failure of support staff to understand the weight of this problem was unbelievable. The Debian Maintainers of ibus made posts to try and help out, but Zoom staff ignored them. I consider this a massive failure from Zoom and a smack in the face for Linux users everywhere. 


