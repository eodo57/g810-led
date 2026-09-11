# Installation :</br>

## Build dependencies :</br>
* git
* g++
* make

## Dependencies :</br>
* hidapi or libusb

For the graphical interface (`g810-led-gui`), additionally:</br>
* gtkmm-3.0 and libepoxy — required</br>
* libpulse — optional, for sound-reactive lighting</br>
* libpipewire-0.3 and glibmm-2.4 — optional, for screen colors</br>
* libayatana-appindicator3 (or libappindicator3) — optional, for the tray icon</br>

Each optional one is compiled out if it is missing, and the window says so
where that feature would have been; none of them stops the GUI building.</br>

## hidapi vs libusb :</br>
hidapi is a newer implementation but needs more testing.</br>
hidapi is more responsive than libusb (~20ms vs ~150ms).</br>
hidapi seems to not work on CentOS, writing to hidraw is not allowed.</br>
hidapi is recommended but if you encounter a problem on your system, switch to libusb.</br>


## Installation using repos :</br>
ArchLinux (aur) :</br>
`yay -S g810-led-git` # with yay</br>
`pacaur -S g810-led-git` # with pacaur</br>
`trizen -S g810-leg-git` # with trizen</br>

Fedora (copr) :<br/>
`sudo dnf copr enable lkiesow/g810-led` # Enable Copr repository<br/>
`sudo dnf install g810-led`<br/>

Gentoo :<br/>
`emerge app-misc/g810-led`<br/>

Debian (unstable, and 10 or later), Ubuntu 19.04 or later :<br/>
`sudo apt install g810-led`

Solus :<br/>
`sudo eopkg install g810-led`<br/>

## Installation of dependencies :</br>
ArchLinux :</br>
`sudo pacman -S git gcc make hidapi` # for hidapi</br>
`sudo pacman -S git gcc make libusb` # for libusb</br>
Debian :</br>
`sudo apt-get install git g++ make libhidapi-dev` # for hidapi</br>
`sudo apt-get install git g++ make libusb-1.0-0-dev` # for libusb</br>
Fedora :</br>
`sudo dnf install git make gcc-c++ hidapi-devel` # for hidapi</br>
`sudo dnf install git make gcc-c++ libusbx-devel` # for libusb</br>
Gentoo :<br/>
`sudo emerge dev-vcs/git dev-libs/hidapi` # for hidapi<br/>
`sudo emerge dev-vcs/git dev-libs/libusb` # for libusb<br/>

## Installation of dependencies for the GUI :</br>
On top of the ones above.</br>
ArchLinux :</br>
`sudo pacman -S gtkmm3 libepoxy` # required</br>
`sudo pacman -S libpulse pipewire glibmm libayatana-appindicator` # optional</br>
Debian / Ubuntu :</br>
`sudo apt-get install libgtkmm-3.0-dev libepoxy-dev` # required</br>
`sudo apt-get install libpulse-dev libpipewire-0.3-dev libglibmm-2.4-dev libayatana-appindicator3-dev` # optional</br>
Fedora :</br>
`sudo dnf install gtkmm30-devel libepoxy-devel` # required</br>
`sudo dnf install pulseaudio-libs-devel pipewire-devel glibmm24-devel libayatana-appindicator-gtk3-devel` # optional</br>

## Installation :</br>
`git clone https://github.com/MatMoul/g810-led.git`</br>
`cd g810-led`</br>
`make bin` # for hidapi</br>
`make bin LIB=libusb` # for libusb</br>
`make gui` # optional, builds the graphical interface</br>
`sudo make install`</br>

`make install` picks up the GUI and its desktop entry only if `make gui` has
been run first, so the command line alone is what you get without it. The
default `make` target does not build the GUI either.</br>

## Installation of the library (For developers) :</br>
`make lib` # for hidapi</br>
`make lib LIB=libusb` # for libusb</br>
`sudo make install-lib` to install the libg810-led library.</br>
`sudo make install-dev` to install the libg810-led library and headers for development.</br>

## Update :</br>
Same as install, but your profile and reboot files are preserved.</br>

## Uninstall :</br>
`sudo make uninstall`</br>
This removes the GUI and its desktop entry as well, whether or not they were
installed.</br>
