# 🦀 Crab Camera Card

[![hacs_badge](https://img.shields.io/badge/HACS-Custom-orange.svg)](https://github.com/hacs/integration)

WORK IN PROGRESS!!!!

An Apple HomeKit-style scrollable camera card for [Home Assistant](https://www.home-assistant.io/).

## ➕ Add to HACS

[![Add to HACS](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=jamesmcginnis&repository=crab-camera-card&category=lovelace)

> Click the button above, or follow the manual steps below.

## Features

- 📹 **Horizontal scrollable row** of camera thumbnails — cameras overflow off-screen just like the HomeKit app
- 🟢 **Live Feed mode** — shows an MJPEG stream directly in each thumbnail
- 🖼️ **Still Image mode** — shows the last snapshot, auto-refreshed at your chosen interval
- 🔍 **Tap to view** — opens a beautiful Apple-style popup with a large live view
- 🔇 **Mute toggle** and **fullscreen button** inside the popup
- 📋 **Long press** — opens the native Home Assistant more-info dialog
- ✨ **Visual Editor** — only shows camera entities; drag to reorder; minimal inputs
- 🟢 **Status dot** — green/grey indicator per camera

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
refresh_interval: 10    # seconds (still mode only)
show_title: true
show_camera_names: true
show_status_dot: true
```

| Option              | Default    | Description |
|---------------------|------------|-------------|
| `entities`          | `[]`       | List of `camera.*` entity IDs |
| `title`             | `Cameras`  | Card header text |
| `show_title`        | `true`     | Show/hide the card title |
| `thumbnail_mode`    | `still`    | `still` for snapshots, `live` for MJPEG stream |
| `refresh_interval`  | `10`       | Seconds between still image refreshes (min 2) |
| `show_camera_names` | `true`     | Show camera name below each tile |
| `show_status_dot`   | `true`     | Show online/offline status indicator dot |

## Usage

| Gesture          | Action |
|------------------|--------|
| **Tap**          | Opens large popup with live view, mute and fullscreen controls |
| **Long press**   | Opens native Home Assistant more-info dialog |
| **Swipe**        | Scroll through cameras horizontally |

## Notes on Live Streams

- **Live Feed thumbnail mode** uses the camera's MJPEG proxy stream (`/api/camera_proxy_stream/`). This works well for most cameras (Frigate, generic MJPEG, etc.).
- For cameras that use HLS or WebRTC natively (e.g. some Unifi/Reolink setups), the popup will attempt to display the MJPEG fallback stream. If your camera doesn't support MJPEG, **Still Image mode** is recommended for thumbnails.
- The **popup viewer** always uses the MJPEG stream. For the best live view experience, use the long-press → more-info route for WebRTC/HLS cameras.

## License

MIT
