# 🦀 Crab Camera Card

[![hacs_badge](https://img.shields.io/badge/HACS-Custom-orange.svg)](https://github.com/hacs/integration)
[![HA Version](https://img.shields.io/badge/Home%20Assistant-2024.1%2B-41BDF5?style=for-the-badge&logo=homeassistant&logoColor=white)](https://www.home-assistant.io/)
![Custom Card](https://img.shields.io/badge/Dashboard-Custom%20Card-white?style=for-the-badge&logo=homeassistant&logoColor=41BDF5)

A scrollable camera card for Home Assistant. Display all your cameras in a horizontal strip — tap to view a full live feed, long-press for the native HA dialog.

---

## Installation via HACS

Click the button below to add this repository to HACS:

[![Add to HACS](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=jamesmcginnis&repository=crab-camera-card&category=plugin)

**Step 1 — Add the custom repository**

Go to **HACS → Frontend → ⋮ → Custom repositories**, enter:

- **Repository:** `https://github.com/jamesmcginnis/crab-camera-card`
- **Category:** Dashboard

Click **Add**, then close the dialog.

**Step 2 — Install**

Search for **Crab Camera Card** in HACS Frontend and click **Download**.

**Step 3 — Add the resource**

Go to **Settings → Dashboards → ⋮ → Resources** and add `/hacsfiles/crab-camera-card/crab-camera-card.js` as a **JavaScript Module**.

---

## Features

- 📹 **Scrollable camera strip** — swipe through all your cameras in a single row
- 🖼️ **Still Image mode** — latest snapshot, auto-refreshed on a configurable interval and on state change
- 🕐 **Timestamp pill** — time the image was last updated, overlaid in the top-right corner of each still thumbnail
- 🟢 **Live Feed mode** — true live stream in each thumbnail (HLS, WebRTC, MJPEG)
- 🔍 **Tap to view** — full-screen popup with live stream, mute toggle and fullscreen button
- 🔇 **Mute toggle** and **⛶ Fullscreen** button in the popup
- 📋 **Long press** — opens the native Home Assistant more-info dialog
- ✨ **Visual Editor** — only live cameras shown; drag-to-reorder; clean minimal settings
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
| `refresh_interval`  | `30`      | Still image polling interval in seconds (min 5) |

---

## Gestures

| Gesture        | Action |
|----------------|--------|
| **Tap**        | Opens full-screen popup with live view |
| **Long press** | Opens native HA more-info dialog |
| **Swipe**      | Scroll through all cameras |
