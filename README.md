# RTEx Link

RTEx Link is a lightweight, offline Android companion app for the **Apache RTX 300** cluster. It records rides, tracks maintenance, and brings Google Maps guidance, calls and music to the cluster without map mirroring or cloud services.

[Download the latest release](https://github.com/smak021/rtex-link/releases/latest)

> This project is independent and is not affiliated with or endorsed by TVS Motor Company or Google. Use at your own risk.

## Features

- Automatic Bluetooth reconnection to the bike.
- Bike ride summary.
- Google Maps turn-by-turn guidance on the cluster, including while the phone is locked.
- Incoming call notifications and call controls on the cluster.
- Music information and play/pause, next and previous controls on the cluster.
- Weekly ride summaries and daily ride timelines.
- Maintenance checkpoints from Garage or a day’s trip view.
- Automatic refill detection and manual refill logging.
- Full-tank and partial refill tracking, measured tank-to-tank mileage and separate gauge estimates.
- Monthly and all-time fuel totals, refill history and recorded spending.
- Maintenance tracking from the latest matching checkpoint.
- Local backup and restore for rides, refuels, maintenance and app preferences.
- No account, ads, analytics or Internet permission.

## Requirements

- Apache RTX 300.
- Android 16 or newer; primarily tested on a Galaxy S23.
- Bluetooth and notification permissions.
- Notification access for navigation and music; phone permissions for call controls.

## Install

1. Download the release APK from [Releases](https://github.com/smak021/rtex-link/releases/latest).
2. Install and open **RTEx Link**, then choose your bike delivery date.
3. Tap **Connect to RTX**, select the bike and allow the requested permissions.
4. Enable notification access for navigation and music.

The app reconnects when the bike becomes available. Do not **Force stop** it; Android blocks background reconnection until you open it again.

## Navigation

1. Connect RTEx Link to the bike once.
2. Start a route in Google Maps.
3. Lock the phone if desired; guidance is relayed to the cluster while connected.

On Samsung phones, keep Google Maps and RTEx Link out of **Sleeping apps** and **Deep sleeping apps**. Power saving can delay navigation updates when the phone is locked.

## Switching to TVS Connect

Tap **Pause companion** in Settings before using TVS Connect. Tap **Resume companion** when returning to RTEx Link.

## Updating and backups

RTEx Link was previously called **RTX Companion**. The package identity is unchanged. Install updates over the existing app with the same signing key to retain your data; do not uninstall or clear storage.

Release and debug APKs have different signing keys. Export a backup from **Settings → Data & backup** before switching build types or phones.

## Privacy and safety

- The journal is stored locally; backups are exported through Android’s file picker.
- No ECU, firmware, diagnostic, immobilizer or vehicle-control operations.
- Navigation may be delayed or incorrect. Follow road signs and use the phone only when safely stopped.
- Bluetooth disconnects can split rides; compatibility varies by phone and cluster.

## To do

- ~~Call notifications and call controls on the cluster.~~
- ~~Music information and playback controls on the cluster.~~
- Outgoing call information and controls on the cluster.
