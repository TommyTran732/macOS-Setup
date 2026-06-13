# macOS-Setup
My notes on how I configure macOS. Some of these settings are for security & privacy, others are just personal preferences.

## Initial installation
- Enable both location services and FileVault. Location services in particular is needed to enable FindMy later.
- Disable Apple Intelligence, Siri, Screen Time, and other AI stuff. (Seriously, who would want this junk on their computer?)

## Setting the UMask
```zsh
sudo launchctl config user umask 077
```

## Date & Time
- Turn off "Set time and date automatically". I will work on enabling NTS later. The default is unsafe.
- Enable 24-hour time
- Enable "Set timezone automatically using your current location". Doesn't really matter because we will turn off location services in a bit, but why not.

## Install script
Run the [macOS Setup Script](https://github.com/TommyTran732/macOS-Setup-Script)

## Configuration Profiles
- Install the Configuration Profiles in this repository
- Enable Lockdown Mode

## Menu bar
- Remove Spotlight
- Add Bluetooth behind WiFi

## System Settings

### iCloud Shenanigans

- Sign into iCloud
- Personal Information
  - Age Range for Apps -> Never
- iCloud
  - Saved to iCloud
    - Drive
      - Sync this Mac
      - Turn off "Desktop & Documents Folder"
      - Turn off "Optimize Mac Storage"
    - Find My Mac
      - Find My Mac: On
      - Find My network: Off
    - Turn everythng else off, especially the Password app
  - Apps syncing to iCloud
    - Turn everything off except Apple Configurator
  - Enable Advanced Data Protection

### Wi-Fi
Ask to join hotspots -> Never

#### Notes
- To prevent malicious actors from setting up fake WiFi networks and track you as you move around, always disable Auto-Join for every network you connect to.
- macOS defaults to using "Fixed" MAC address randomization, which allows access points to track when your specific device connects to them. Always set the "Private Wi-Fi address" to "random". Annoyingly, macOS allows you to set this when you are connected to the SSID, so you can't really manage it after the fact without disabling SIP and editing `/Library/Preferences/SystemConfiguration/com.apple.airport.preferences.plist` (I think).

### Network
Thunderbolt Bridge -> Delete Service

### Battery
- Options
  - Wake for network access -> Never (Only on power is quite buggy, as it will keep accessing Wi-Fi after it has been turned off and unplugged).    

### General
- Storage
  - Enable "Empty Trash automatically"

### Desktop & Dock
Turn off show suggested and recent apps in Dock

### Lock Screen
- Turn display off when power adatper is active -> For 5 minutes
- Require password after screen saver begins or display is turned off -> Immediately
- Show message when locked -> "If lost, please contact <email>"

### Privacy & Security
- Location Services -> Turn everything off (including Find My Mac), except Setting time zone
- Turn off location services
- Apple intelligence report -> Report Duration Off
- Background security improvements -> On

### Spotlight
- Turn off show related content
- Turn off help apple improve search
- Disable all results from apps
- Disable all results from system, except for "Apps"

### Trackpad
- Secondary click -> Click in Bottom Right Corner
- Enable "Tap to click"

## Activity Monitor
View -> Enable both the "Sandbox" and "Restricted" columns.

## Audio MIDI Setup
Microphone -> Mute (Probably theatre because TCC already exists, but still)

## Finder
- General -> Uncheck all items under "Show these items on the desktop" 
- Advanced -> Show all filename extensions

## Passwords
- Save passwords: Do Not Ask When Signing In
- Uncheck all options, especially "Detect Compromised Passwords"

## Terminal
- Settings
  - Secure Keyboard Entry

## Safari
- Main Screen
  - Remove all favorites
  - Edit -> Disable everything except privacy report
- General
  - Safari opens with a new private window
  - Remove history items after 1 day
- Autofill
  - Disable all
- Search
  - Search engine -> DuckDuckGo
  - Disable all SmartSearch options
- Security
  - Enable "Warn before connecting to a website over HTTP"
- Advanced
  - Use advanced tracking and fingerprinting protection -> in all browsing
  - Uncheck "Allow websites to check for Apple Pay and Apple card"
  - Uncheck "Allow privacy-preserving measurement of ad effectiveness"

## Unsandboxed Apps
- Install GPG Tools, IVPN, Microsoft Edge, Microsoft Office (only the updater is unsandboxed, all office apps are), and VMWare Fusion.

- Microsoft Edge:
  - Unpin favorites
  - Profiles -> Profile Preferences -> Turn of allow single sign-on for work or school sites
  - Privacy, search, and services
    - Security -> Turn off protect from harmful sites and downloads (The policy to turn it off by default does not work without a real MDM).
    - Search and connected experiences -> Switch to DuckDuckGo

## Virtual Machines
VMWare Fusion is the primary VM Manager.

Compared to UTM:
- It can suspend the VM even with GPU acceleration, making it much more usable.

Compared to Parallels:
- VMWare Linux drivers are open source and available on most distributions. There is no need for a custom kernel module and installer like Parallels, and it works nicely with Fedora Atomic too.

## Clean Up
- Go through Privacy & Security and disable all unnecessary permissions. Annoyingly, VMWare Fusion will complain about Accessibility every start up if it is not allowed the permission.
- Check "Saved to iCloud" "Apps syncing to iCloud" and make sure no apps turn it on after first launch, except for Apple Configurator.
