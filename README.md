# 🦀 Crab Camera Card

[![hacs_badge](https://img.shields.io/badge/HACS-Custom-orange.svg)](https://github.com/hacs/integration)

A scrollable camera card for [Home Assistant](https://www.home-assistant.io/). Display all your cameras in a horizontal strip — tap to view a full live feed, long-press for the native HA dialog.

## ➕ Add to HACS

[![Add to HACS](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=jamesmcginnis&repository=crab-camera-card&category=lovelace)

> Click the button above, or follow the manual steps below.

## Features

- 📹 **Horizontal scrollable strip** — cameras overflow off-screen so you can swipe through them
- 🖼️ **Still Image mode** — displays the latest snapshot, updated automatically whenever Home Assistant refreshes the camera
- 🟢 **Live Feed mode** — renders a true live stream in each thumbnail using Home Assistant's own stream component (supports HLS, WebRTC and MJPEG)
- 🔍 **Tap to view** — opens a full-screen popup with a live stream, mute toggle and fullscreen button
- 📋 **Long press** — opens the native Home Assistant more-info dialog
- ✨ **Visual Editor** — only live-capable cameras shown; drag to reorder; minimal inputs
- 🟢 **Status dot** — green (live), yellow (still), red (offline) per camera

## Installation via HACS

1. In HACS → **Frontend** → click the ⋮ menu → **Custom repositories**
2. Add `https://github.com/jamesmcginnis/crab-camera-card` as a **Lovelace** repository
3. Install **Crab Camera Card**
4. Add the card resource, or let HACS do it automatically

## Manual Installation

1. Download `crab-camera-card.js` from [the latest release](https://github.com/jamesmcginnis/crab-camera-card/releases)
2. Copy to `/config/www/crab-camera-card.js`
3. Add as a Lovelace resource:
   ```yaml
   url: /local/crab-camera-card.js
   type: module
   ```

## Configuration

```yaml
type: custom:crab-camera-card
title: Cameras
entities:
  - camera.front_door
  - camera.back_garden
  - camera.garage
thumbnail_mode: still   # still | live
show_title: true
show_camera_names: true
show_status_dot: true
```

| Option              | Default    | Description |
|---------------------|------------|-------------|
| `entities`          | `[]`       | List of `camera.*` entity IDs |
| `title`             | `Cameras`  | Card header text |
| `show_title`        | `true`     | Show/hide the card title |
| `thumbnail_mode`    | `still`    | `still` for snapshots, `live` for streaming thumbnails |
| `show_camera_names` | `true`     | Show camera name below each tile |
| `show_status_dot`   | `true`     | Show status indicator dot on each tile |

## Usage

| Gesture        | Action |
|----------------|--------|
| **Tap**        | Opens full-screen popup with live view, mute and fullscreen controls |
| **Long press** | Opens native Home Assistant more-info dialog |
| **Swipe**      | Scroll through cameras horizontally |

## Status Dots

| Colour | Meaning |
|--------|---------|
| 🟢 Green  | Live mode — camera online |
| 🟡 Yellow | Still mode — camera online |
| 🔴 Red    | Camera offline or unavailable |

## Notes

- **Still mode** images update automatically whenever Home Assistant refreshes the camera entity — no polling interval is needed or configurable.
- **Live mode** thumbnails use `ha-camera-stream`, the same component HA uses internally, so HLS, WebRTC and MJPEG cameras all work without any extra configuration.
- The visual editor only lists cameras that support live streaming. Snapshot-only, recording clip and sensor cameras are excluded automatically.

## License

MIT
