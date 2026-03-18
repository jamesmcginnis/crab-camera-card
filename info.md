# 🦀 Crab Camera Card

[![hacs_badge](https://img.shields.io/badge/HACS-Custom-orange.svg)](https://github.com/hacs/integration)

An Apple HomeKit-style scrollable camera card for Home Assistant. Display all your cameras in a horizontal scrollable row — tap to view a large live feed, long-press for the native HA dialog.

## ➕ Add to HACS

[![Add to HACS](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=jamesmcginnis&repository=crab-camera-card&category=lovelace)

> Click the button above, or manually add `https://github.com/jamesmcginnis/crab-camera-card` as a custom Lovelace repository in HACS.

---

## Features

- 📹 **Scrollable camera strip** — cameras scroll off the sides just like Apple HomeKit
- 🖼️ **Still Image mode** — last snapshot, auto-refreshed at your chosen interval
- 🟢 **Live Feed mode** — MJPEG stream shown directly in each thumbnail
- 🔍 **Tap to view** — Apple-style frosted popup with a large live view
- 🔇 **Mute toggle** and **⛶ Fullscreen** button in the popup
- 📋 **Long press** — opens the native Home Assistant more-info dialog
- ✨ **Visual Editor** — only camera entities shown; drag-to-reorder; minimal inputs
- 🟢 **Status dot** — glowing green = online, grey = unavailable

---

## Quick Config

```yaml
type: custom:crab-camera-card
title: Cameras
entities:
  - camera.front_door
  - camera.back_garden
  - camera.garage
thumbnail_mode: still   # still | live
refresh_interval: 10    # seconds (still mode only)
```

| Option              | Default   | Description |
|---------------------|-----------|-------------|
| `entities`          | `[]`      | Camera entity IDs |
| `title`             | `Cameras` | Card header text |
| `show_title`        | `true`    | Show/hide card title |
| `thumbnail_mode`    | `still`   | `still` or `live` |
| `refresh_interval`  | `10`      | Still image refresh in seconds |
| `show_camera_names` | `true`    | Camera name below each tile |
| `show_status_dot`   | `true`    | Online/offline indicator |

---

## Gestures

| Gesture        | Action |
|----------------|--------|
| **Tap**        | Opens Apple-style popup with live view |
| **Long press** | Opens native HA more-info dialog |
| **Swipe**      | Scroll through all cameras |
