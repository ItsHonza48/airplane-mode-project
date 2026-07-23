# Custom Airplane Mode for Linux (Macbook Pro 2011)

This is a bash script that is quite light i would say. I designed this to maximize battery length during long flights on older laptops running Linux (I specifically tested this on Linux Mint 22.3 and a 2011 MacBook Pro 13 inch model). I created this as a project for HackClub and me because i wanted the longest battery health for my flight to Egypt.

## What it does
- **airplane-mode:** Turns off wifi ethernet and Bluetooth it also disables Intel Turbo Boost to prevent the CPU from overclocking and draining the battery.
- **normal-mode:** Turns the wifi, ethernet and bluetooth back on again with 'rfkill', it also re-enables Intel Turbo Boost for full performance.

## Requirements/best compatibility 
- Linux Mint or Ubuntu or any Debian-based distro
- Intel Processor (with 'intel_pstate' support) for turning off the turbo boost
- NetworkManager ('nmcli') and BlueZ ('bluetoothctl') installed so it can turn off and on the bluetooth and wifi.

## Instalation

## You should first clone this repo with
```bash
git clone https://github.com/ItsHonza48/airplane-mode-project.git
cd airplane-mode-project

## Then you should build the Debian package or download the release from this repo
Run the package manager tool to bundle the DEBIAN and usr folders into a single installable .deb file:
dpkg-deb --build . airplane-mode.deb

## After that the last step is to install it  globally
Install the generated package using dpkg:
sudo dpkg -i airplane-mode.deb

## How to run
Once you installed it, You can open the Gui in your terminal using the command airplane-mode-gui. Any user can use it after you installed it globally.

## How to check if it actually works 

You can check if the Intel Turbo Boost is really disabled by running this command in your terminal:
```bash
cat /sys/devices/system/cpu/intel_pstate/no_turbo

If it returns 1, Turbo Boost is DISABLED (Airplane mode is active).

If it returns 0, Turbo Boost is ENABLED (Normal mode is active).

## Compatibility with Slimbook Battery


This script/command works very good or perfectly with tools like Slimbook Battery.
When you activate airplane-mode, the CPU is capped regardless of your Slimbook profile.
For maximum battery saving during your flight, it is recommended to turn on  Slimbook Battery energy saving mode manually via the tray icon, though the script handles the most things that eat the battery like i said wifi bluetooth intel overclock and ethernet.

## Credits
* I Developed this and also vibecoded with gemini i did almost all the work but didn't understand the Turbo Boost part and i didn't know how to compile this it also helped me with optimizing the script so there are less lines if i did it myself.
