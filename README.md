# Custom Airplane Mode for Linux (Macbook Pro 2011)

This is a lightweight bash script project designed to maximize battery life during long flights on older laptops running Linux (specifically tested on Linux Mint and a 2011 MacBook Pro). Created as a project for HackClub and me because i wanted the longest battery health for my flight to Egypt.

## What it does
- **airplane-mode:** Instantly disables all network interfaces (Wi-Fi and Ethernet), powers down Bluetooth, and disables Intel Turbo Boost to prevent the CPU from overclocking and draining the battery.
- **normal-mode:** Unblocks wireless devices using 'rfkill', restores Wi-Fi and Bluetooth connections, and re-enables Intel Turbo Boost for full performance.

## Requirements
- Linux Mint / Ubuntu / Debian-based distros
- Intel Processor (with 'intel_pstate' support)
- NetworkManager ('nmcli') and BlueZ ('bluetoothctl') installed

## Instalation and Usage

1. Clone or download this repo to your drive.
2. Open your terminal in the project directory and make the scripts executable:
```bash
chmod +x airplane-mode normal-mode

3. Before takeoff, run the airplane mode script:
sudo ./airplane-mode

4. After landing, restore your settings back to normal:
sudo ./normal-mode

## How to verify it works

You can check if Intel Turbo Boost was succesfully disabled by running this command in your terminal:
```bash
cat /sys/devices/system/cpu/intel_pstate/no_turbo

If it returns 1, Turbo Boost is DISABLED (Airplane mode is active).

If it returns 0, Turbo Boost is ENABLED (Normal mode is active).

## Compatibility with Slimbook Battery


This script works perfectly with tools like **Slimbook Battery**.
When you activate `airplane-mode`, the CPU Turbo Boost is strictly capped regardless of your Slimbook profile.
For maximum battery savings during flight, it is recommended to switch Slimbook Battery to **Energy Saving** mode manually via the tray icon, though the script handles the most power-hungry components (Wi-Fi, Bluetooth, and Turbo Boost) automatically.