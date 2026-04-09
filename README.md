# 🦀 Crab Camera Card

[![hacs_badge](https://img.shields.io/badge/HACS-Custom-orange.svg)](https://github.com/hacs/integration)
[![HA Version](https://img.shields.io/badge/Home%20Assistant-2024.1%2B-41BDF5?style=for-the-badge&logo=homeassistant&logoColor=white)](https://www.home-assistant.io/)
![Custom Card](https://img.shields.io/badge/Dashboard-Custom%20Card-white?style=for-the-badge&logo=homeassistant&logoColor=41BDF5)

A scrollable camera card for [Home Assistant](https://www.home-assistant.io/). Display all your cameras in a horizontal strip — tap to view a full live feed, long-press for the native HA dialog.

---

## 🚀 Installation

### Via HACS (Recommended)

Click the button below to add this repository to HACS:

[![Add to HACS](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=jamesmcginnis&repository=crab-camera-card&category=plugin)

Then:

1. Open **HACS** in Home Assistant
2. Go to **Frontend**
3. Search for **Crab Camera Card**
4. Click **Download**
5. Reload your browser

### Manual Installation

1. Download `crab-camera-card.js` from the [latest release](../../releases/latest)
2. Copy it to `/config/www/crab-camera-card.js`
3. In Home Assistant go to **Settings → Dashboards → Resources**
4. Add a new resource:
   - URL: `/local/crab-camera-card.js`
   - Type: **JavaScript module**
5. Reload your browser

---

## ✨ Features

- 📹 **Horizontal scrollable strip** — cameras overflow off-screen so you can swipe through them
- 🖼️ **Still Image mode** — displays the latest snapshot; auto-refreshes on a configurable interval and whenever Home Assistant detects a state change
- 🕐 **Timestamp pill** — each still image shows the time it was last updated, overlaid in the top-right corner of the thumbnail
- 🟢 **Live Feed mode** — renders a true live stream in each thumbnail using Home Assistant's own stream component (supports HLS, WebRTC and MJPEG)
- 🔍 **Tap to view** — opens a full-screen popup with a live stream, mute toggle and fullscreen button
- 📋 **Long press** — opens the native Home Assistant more-info dialog
- ✨ **Visual Editor** — only live-capable cameras shown; drag to reorder; minimal inputs
- 🔴🟡🟢 **Status dot** — red (offline), yellow (still mode), green (live mode) per camera

---

## 🛠️ Configuration

Add a new card to your dashboard, choose **Manual** and use:

```yaml
type: custom:crab-camera-card
title: Cameras
entities:
  - camera.front_door
  - camera.back_garden
  - camera.garage
thumbnail_mode: still   # still | live
```

### All Options

| Option              | Default    | Description |
|---------------------|------------|-------------|
| `entities`          | `[]`       | List of `camera.*` entity IDs |
| `title`             | `Cameras`  | Card header text |
| `show_title`        | `true`     | Show/hide the card title |
| `thumbnail_mode`    | `still`    | `still` for snapshots, `live` for streaming thumbnails |
| `show_camera_names` | `true`     | Show camera name below each tile |
| `show_status_dot`   | `true`     | Show status indicator dot on each tile |
| `refresh_interval`  | `30`       | How often (in seconds) to poll for a new still image. Minimum 5s. |

### Full Example

```yaml
type: custom:crab-camera-card
title: Cameras
entities:
  - camera.front_door
  - camera.back_garden
  - camera.garage
thumbnail_mode: still
show_title: true
show_camera_names: true
show_status_dot: true
refresh_interval: 30
```

---

## 👆 Gestures

| Gesture        | Action |
|----------------|--------|
| **Tap**        | Opens full-screen popup with live view, mute and fullscreen controls |
| **Long press** | Opens native Home Assistant more-info dialog |
| **Swipe**      | Scroll through cameras horizontally |

---

## 🔴🟡🟢 Status Dots

| Colour | Meaning |
|--------|---------|
| 🟢 Green  | Live mode — camera online |
| 🟡 Yellow | Still mode — camera online |
| 🔴 Red    | Camera offline or unavailable |

---

## 🕐 Timestamp Pill

In still image mode, each thumbnail displays a small frosted-glass pill in the top-right corner showing the time the image was last updated. The time is sourced from the companion still/recording entity where one exists (e.g. `camera.back_garden_last_recording`), falling back to the camera entity itself. The pill updates automatically each time the image refreshes.

---

## 📝 Notes

- **Still mode** images refresh automatically on state change and on the configured `refresh_interval`. The interval also resets immediately after you close the live popup so you always see the latest frame.
- **Live mode** thumbnails use `ha-camera-stream`, the same component HA uses internally, so HLS, WebRTC and MJPEG cameras all work without any extra configuration.
- The visual editor only lists cameras that support live streaming. Snapshot-only, recording clip and sensor cameras are excluded automatically.
- **Companion still entities** — if your live camera has a linked recording or snapshot entity (e.g. `camera.front_door_last_recording`), the card will automatically use that entity's image for the still thumbnail and timestamp.

---

## 📄 License

MIT
