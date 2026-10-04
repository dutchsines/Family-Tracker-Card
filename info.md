# Family Tracker Card

A custom Lovelace card for Home Assistant designed to track family members' locations, custom zones, battery levels, charging status, and historical timeline movements in a clean, modern card interface.

## Features

- **Live Location Tracking**: Real-time display of current zones, custom states, and live driving speeds.
- **Battery & Charging Indicators**: Configurable phone and watch battery tracking with dynamic color coding and low-battery pulse animations.
- **Interactive History Timeline**: Visual horizontal breakdown of location history over a customizable time range (default 8 hours).
- **Native Popup Integration**: Clicking a person's name, badge, or battery pill opens the native Home Assistant `more-info` dialog.
- **Visual Card Editor**: Fully supported through the Home Assistant UI card editor with custom zone auto-importing.
- **Customizable Styling**: Compact mode, glassmorphism blur effects, custom border radii, text scaling, and gradient bars.

## Installation (HACS)

1. Open **HACS** in your Home Assistant instance.
2. Go to **Frontend**.
3. Click the three dots in the top right and select **Custom repositories**.
4. Add your repository URL (`https://github.com/dutchsines/family-tracker-card`) and select **Lovelace** as the category.
5. Install the **Family Tracker Card** and refresh your browser.
## Manual Installation

1. Download `family-tracker-card.js` from the repository and place it in your `www` folder (e.g., `/config/www/family-tracker-card.js`).
2. Add the resource reference in your Home Assistant dashboard settings or via YAML:
   ```yaml
   resources:
     - url: /local/family-tracker-card.js
       type: module
   type: custom:family-tracker-card
      ```
```yaml
title: "Family Presence"
hours_to_show: 8
show_timeline: true
show_driving_speed: true
use_gradient_bar: true
people:
  - name: "Dutch"
    tracker: "device_tracker.life360_dutch_sines"
    phone_batt: "sensor.pixel_10_pro_battery_level"
    phone_state: "sensor.pixel_10_pro_battery_state"
    watch_batt: "sensor.pixel_watch_3_battery_level"
    watch_state: "sensor.pixel_watch_3_battery_state"
  - name: "Ayden"
    tracker: "device_tracker.life360_ayden_eccles"
    phone_batt: "sensor.ayden_pixel_10_pro_battery_level"
    phone_state: "sensor.ayden_pixel_10_pro_battery_state"
    watch_batt: "sensor.ayden_pixel_watch_3_battery_level"
    watch_state: "sensor.ayden_pixel_watch_3_battery_state"
custom_locations:
  - state: "home"
    label: "Home"
    color: "#4CAF50"
    icon: "🏠"
  - state: "driving"
    label: "Driving"
    color: "#E53935"
    icon: "🚗"
