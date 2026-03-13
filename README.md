# tETHer - ethernet tethering
Tether one device to another over an ethernet interface on linux (rather than USB)

Tethering proxies one device through another devices internet connections. A common use case is to connect to a mobile phone over USB and then use its internet connection. tETHer does the same thing but via an ethernet connection such as an rj-45 cable.

This also allows forwarding

## Motivation
I had a camera which only supported wired connection. I did not want to run a long wire to a router and wireless bridges were moderately expensive so I decided to get this working with an old raspberry pi. I don't really like "infrastructure" because I forget how it works. I prefer tools which minimise the amount of infrastructure so I coded this.

## Alterantives and prior work
Use a wireless bridge.  Hand code the networking yourself using wireless.

This is very similar to the idea of setting up an *access point*, but it has some additional features for port forwarding which are made easier if you are providing access or a single device.

## Installation
tETHer requires `nmap` `dnsmasq` and Linux. On a linux machine install them: `sudo apt install nmap dnsmasq` pipx.

You can then install with pipx: `pipx install tETHer`

## Usage
Set up dhcp and forwarding on eth0 so that if you plug in a device which uses DHCP it will connect to you and then via you to the rest of the network - including the internet.

`eth-tether eth0`

If you want to forward ports you can capture all the ports that the tethering machine has

`eth-tether eth0 --scan ports`

Then on subsequent files you can use the generated ports file

`eth-tether eth0 --ports ports`

To avoid requiring too many permissions, tETHer uses sudo to run privileged commands. You can allow your use to only run these commands or you can run the entire commadn with sudo. To get a sudoers file alowing these commands run `eth-tether eth0 --sudoers`


