# RTEx Link

Your rides, your bike, your maintenance—in one offline Android companion for the **TVS Apache RTX 300**.

RTEx Link connects to the motorcycle’s Bluetooth cluster to display bike readings, record trips, relay Google Maps directions, and provide call and music integration. **Garage** keeps refuels, tyres and service history together, with maintenance intervals based on your bike’s odometer and delivery date.

**[Download the latest release](https://github.com/smak021/rtex-link/releases/latest)** · [All releases](https://github.com/smak021/rtex-link/releases)

> Independent community project. Not affiliated with or endorsed by TVS Motor Company or Google. Compatibility is currently focused on the Apache RTX and Android 16; use at your own risk.

## At a glance

| Area | What you can do |
| --- | --- |
| **Bike** | See connection status and available bike readings, review the last ride, and open turn-by-turn navigation. |
| **Trips** | Review weekly totals and daily ride timelines, inspect recording gaps, and add maintenance checkpoints to a day. |
| **Garage** | Track fuel, tyres, service visits, costs and upcoming maintenance. |
| **Settings** | Configure delivery date, maintenance intervals, calls, music, navigation, notifications and local backups. |

## Getting started

### Requirements

- TVS Apache RTX 300 with its compatible Bluetooth cluster.
- Android 16 or newer. The primary validation phone is a Samsung Galaxy S23.
- Bluetooth permissions for pairing and connection, plus notification permission for connection and maintenance notifications.
- Notification access for Google Maps guidance and music integration. Optional phone permissions are used for call controls.

### Install and connect

1. Download the **release APK** and checksum file from [Releases](https://github.com/smak021/rtex-link/releases/latest).
2. Install and open **RTEx Link**. Choose your bike delivery date when asked; you can change it later in Settings.
3. Tap **Connect to RTX**, select your bike, and allow the required permissions.
4. Enable notification access if you want navigation or music integration, and grant phone permissions if you want call controls.

After the first pairing, the app reconnects when the bike becomes available. Android **Force stop** prevents background reconnection until you open the app again.

To verify a downloaded APK on Linux or macOS, run the checksum command from the directory containing both release files:

```sh
sha256sum -c RTEx-Link-v0.5.1.apk.sha256
```

### Updating an existing installation

**RTEx Link was previously named RTX Companion.** The Android package remains `dev.rtx.companion`, so the rename preserves the existing journal and preferences when installed as an update with the matching signing key.

Install over the existing app; do not uninstall or clear storage. Release and debug APKs use different signing keys. A release APK cannot directly replace a debug installation. Export a backup before switching build types or phones.

## Trips and recording coverage

Trips shows your last seven days and a list of recent days. Open a day to review each ride’s start/end times, distance, duration and available readings. Maintenance checkpoints appear alongside the rides, and **Add checkpoint** lets you log work directly from that day.

- Each recorded ride corresponds to a Bluetooth connection session. Disconnected sessions are not silently joined.
- **Unrecorded distance** uses plausible odometer gaps to show distance missing from recorded trips. It does not invent routes or telemetry.
- Odometer **+ / −** controls step through the recorded ride boundaries shown in day details. You can also enter an odometer manually.
- Checkpoint dates can be matched from recorded odometers. When the date cannot be established reliably, choose it manually.

Fuel and maintenance distances use odometer readings, so distance ridden without the phone can still count when the app receives an updated odometer.

## Garage

Garage has four sections: **Overview**, **Fuel**, **Tyres** and **Service**. Use **Add maintenance checkpoint** to choose a maintenance type from a searchable, grouped list.

### Overview and upcoming work

**Coming up** shows overdue and upcoming tasks with distance or days remaining. Distance-based items are ordered by kilometres left, with overdue work first; imminent calendar deadlines are also prioritised. Days and kilometres are treated as different units.

Monthly summaries bring together refuels, tyre mileage and known maintenance spending.

### Fuel and refuels

- Log a refill manually or tap an automatically detected refill to add the actual litres filled.
- Mark a **full tank** or partial top-up, and optionally record cost and notes.
- Your entered litres take precedence over the gauge estimate for that same refill.
- Browse the refill log grouped by month, with refill counts, litres and recorded spending, plus all-time totals and monthly comparisons.
- Review distance since the last refill and between refills using odometer readings.

**Measured tank-to-tank economy** needs two confirmed full tanks and measured litres for every refill after the starting full tank through the ending full tank, including partial top-ups. The starting tank’s litres are excluded:

```text
km/L = (ending full-tank odometer − starting full-tank odometer)
       ÷ litres added after the starting fill, through the ending fill
```

Fuel-gauge economy is a separate approximate figure using gauge readings and the nominal tank capacity. The bike-reported mileage is also separate. Missing litres or prices are not presented as measured totals.

### Tyres

Track front and rear tyres separately: model, fitting date and odometer, distance since installation, optional mileage target, and the previous tyre’s lifespan.

A tyre with no recorded replacement is treated as the original stock tyre from **0 km**. Logging its first replacement preserves that tyre’s distance travelled.

### Maintenance checkpoints

Log chain lube, tyre pressure checks, tyre changes, oil changes, chain work, brakes, servicing and other work. Save the date, odometer, optional cost and notes; edit existing entries when needed.

The latest matching checkpoint becomes the baseline for that maintenance interval. Without one, the baseline is **0 km** and your **bike delivery date**. Saving a completed job updates its due calculation and clears its stale due notification.

### Numbered service visits

In **Garage → Service**, choose **Log service visit** to record the 1st, 2nd or later planned service as one pack.

- Standard scheduled jobs are **preselected** using the TVS owner’s manual. Review the checklist and keep only work actually completed.
- Optional chain lube and annual brake-fluid replacement stay unchecked unless you select them.
- Inspection, top-up and replacement are distinct operations. An inspection does not reset a replacement interval.
- Enter individual job prices, labour, other charges/tax, and an optional invoice total.
- The service counts as **one bill**; linked job prices are not counted again in the overall spending total.
- Editing or deleting a service visit updates its linked jobs together. Standalone oil changes, lube and other checkpoints remain available.

Numbered visits advance the planned service timeline; an oil change or chain lube by itself does not. The manual’s first 11 visits use distance or time from delivery, whichever comes first. Later visits are labelled as a continuation of the periodic cadence. The first three visits are labour-free; chargeable materials and actual prices still depend on the work and invoice.

The app does not reset or synchronize the cluster’s service reminder.

Source: [TVS Apache RTX owner’s manual](https://www.tvsmotor.com/-/media/Feature/Owners/25-11-25/TVS-Apache-RTX.pdf).

### Intervals and local reminders

Open **Intervals** from Garage or the maintenance setup in Settings to enable tasks and adjust distance and time limits. Expand a task to edit its values, use presets, or remove a limit, then tap **Save intervals**.

Examples include chain lube every **500 km** and tyre pressure checks every **14 days**. These are editable intervals, not a substitute for the owner’s manual or inspection. Where both distance and time are configured, the first limit reached controls when the task is due.

Maintenance notifications run locally through Android background checks and new bike readings—no Firebase or cloud account is required. Allow notification permission and enable maintenance notifications in Settings. Android may delay background checks; distance-based reminders need an updated odometer.

## Navigation, music and calls

### Google Maps guidance

Open **Turn-by-turn** from Bike and enable notification access. Start a route in Google Maps; guidance is relayed to the cluster while connected, including when the phone is locked. After pairing, you do not need to open RTEx Link for every route.

On Samsung phones, keep Google Maps and RTEx Link out of **Sleeping apps** and **Deep sleeping apps**. Power saving can delay locked-screen navigation updates.

### Music

With notification access enabled and an active Android media session, the app relays track title, artist and playback state. Supported cluster controls send play/pause, next and previous commands to that session. Behaviour depends on the player and cluster; live compatibility testing remains ongoing. Music metadata is held in memory.

### Calls

Incoming call notifications and cluster call controls are implemented, with the required phone permissions. Outgoing call information and controls remain planned.

### Switching to TVS Connect

In **Settings**, tap **Pause companion** before using the official TVS Connect app. Tap **Resume companion** when returning to RTEx Link. Avoid having both apps control the cluster connection simultaneously.

## Backup and restore

Open **Settings → Data & backup** to export a portable JSON file or restore one through Android’s file picker.

Backups include trips, recorded readings, refuels, maintenance, linked service jobs, tyre details, intervals, delivery date and supported app preferences. They exclude pairing credentials, caller information and live navigation.

Restore validates and previews the backup, creates a pre-restore safety copy, and merges missing records without duplicating them. Existing manual entries are kept; conflicting service visits are retained as complete local groups. Older backup formats remain supported. Bluetooth pairing must be established on the destination phone. The current backup size limit is **50 MB**.

Backups are manual and local—choose your own storage location and keep a copy before changing phones or build types.

## Privacy and compatibility

- No account, ads, analytics, cloud backend or Internet permission.
- Local storage for the journal and preferences; files leave the app when you export them.
- Google Maps and music playback continue to use their respective apps and permissions.
- No ECU, firmware, immobilizer, diagnostic or vehicle-control operations. The app relays supported display and phone information only.
- Navigation may be delayed or incorrect. Follow road signs and operate the phone only when safely stopped.
- Bluetooth interruptions can split a ride. Compatibility outside the tested phone and cluster is not guaranteed.

## Roadmap

- ~~Call notifications and call controls on the cluster.~~
- ~~Music information and playback controls on the cluster.~~
- Outgoing call information and controls on the cluster.
