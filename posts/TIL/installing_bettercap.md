###### [Home](https://eduardo-granados.github.io/)

---

# Installing Bettercap on Kali Linux


I was having some minor issues trying to get Bettercap installed by following the guide.

In order to compile bettercap from sources, make sure that you install the dependencies:

build-essential
libpcap-dev
libusb-1.0-0-dev (required by the HID module)
libnetfilter-queue-dev (on Linux only, required by the packet.proxy module)
Once you’ve met this conditions, you can run the following commands to compile and install bettercap in /usr/local/bin/bettercap:

Next, with the installation 


`sudo apt update`

`sudo apt install build-essential libpcap-dev libusb-1.0-0-dev libnetfilter-queue-dev`

after installing the dependencies, traverse to the "etc/" directory to clone Bettercap

`git clone github.com/bettercap/bettercap`

lastly

`sudo make build`

`sudo make install`