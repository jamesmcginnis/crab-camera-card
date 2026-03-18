# 🦀 Crab Camera Card

[![hacs_badge](https://img.shields.io/badge/HACS-Custom-orange.svg)](https://github.com/hacs/integration)

A scrollable camera card for Home Assistant. Display all your cameras in a horizontal strip — tap to view a full live feed, long-press for the native HA dialog.

## ➕ Add to HACS

[![Add to HACS](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=jamesmcginnis&repository=crab-camera-card&category=lovelace)

> Click the button above, or manually add `https://github.com/jamesmcginnis/crab-camera-card` as a custom Lovelace repository in HACS.

---

## Features

- 📹 **Scrollable camera strip** — swipe through all your cameras in a single row
- 🖼️ **Still Image mode** — latest snapshot, updated automatically by Home Assistant
- 🟢 **Live Feed mode** — true live stream in each thumbnail (HLS, WebRTC, MJPEG)
- 🔍 **Tap to view** — full-screen popup with live stream, mute toggle and fullscreen button
- 🔇 **Mute toggle** and **⛶ Fullscreen** button in the popup
- 📋 **Long press** — opens the native Home Assistant more-info dialog
- ✨ **Visual Editor** — only live cameras shown; drag-to-reorder; no unnecessary settings
- 🔴🟡🟢 **Status dot** — red (offline), yellow (still mode), green (live mode)

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
```

| Option              | Default   | Description |
|---------------------|-----------|-------------|
| `entities`          | `[]`      | Camera entity IDs |
| `title`             | `Cameras` | Card header text |
| `show_title`        | `true`    | Show/hide card title |
| `thumbnail_mode`    | `still`   | `still` or `live` |
| `show_camera_names` | `true`    | Camera name below each tile |
| `show_status_dot`   | `true`    | Status indicator dot |

---

## Gestures

| Gesture        | Action |
|----------------|--------|
| **Tap**        | Opens full-screen popup with live view |
| **Long press** | Opens native HA more-info dialog |
| **Swipe**      | Scroll through all cameras |
