# My Home Assistant Configuration
## Overview
This is my HomeAssistant configuration.

The main goal was to have the day-to-day activations and information immediately visible and everything else (like schedulers, history graphs) available upto 1-click away.
My main interface with the systen is via two wall mounted DIY 15.6 RaspberryPi based touchscreens. One on each floor.

You can take a glance at the functionality in the below video (although not up-to-date):

[![Floorplan](ScreenShots/floorplan.png?raw=true)](https://www.youtube.com/watch?v=o_AKHEyWXR0)

The UI is defined in the *lovelace_new_data.yaml* file.
Each section has a header and implements a different part of the UI.

All house images were created using SweetHome3D software and manipulated using GIMP image editing SW.
Two main floorplan images are the starting point:
* All lights OFF
* All light ON - from there each light ON image was created seperately

Only custom cards can be displayed on the UI so if an internal HA card need to be shown then a custom card template should be used as wrapper.

## Table of Contents
- [My Home Assistant Configuration](#my-home-assistant-configuration)
  - [Overview](#overview)
  - [Table of Contents](#table-of-contents)
  - [UI Explained](#ui-explained)
    - [Definition](#definition)
    - [Macros](#macros)
    - [Start](#start)
    - [Pictures](#pictures)
    - [Weather](#weather)
    - [Calendar](#calendar)
    - [Lights](#lights)
      - [Light Entity](#light-entity)
      - [Light Group](#light-group)
    - [Covers](#covers)
      - [Cover Entity](#cover-entity)
      - [Cover Group](#cover-group)
    - [Irrigation](#irrigation)
      - [Irrigation Entity](#irrigation-entity)
      - [Irrigation Group](#irrigation-group)
    - [Temperature Sensors](#temperature-sensors)
    - [Water Boiler](#water-boiler)
    - [Vacuums](#vacuums)
    - [Media Players](#media-players)
    - [HVAC](#hvac)
    - [Navigation](#navigation)
    - [Status Bar](#status-bar)
    - [Settings](#settings)
    - [UnRaid](#unraid)
    - [Water](#water)
    - [Actions](#actions)
    - [Conditional Entity](#conditional-entity)
    - [Refresh Reload](#refresh-reload)
  - [Sources](#sources)
    - [Integrations](#integrations)
    - [Custom Cards](#custom-cards)
  - [Support](#support)
  
## UI Explained

### Definition
Contains parameters and settings for the UI to easily change the look&feel of the UI.
Includes lists of entities and their parameters for placement, icons, actions, etc...

### Macros
Contains "functions" to simplify reoccuring UI elements.

### Start
Defines the background image of the house with transparecny in all areas outside the floorplan boundaries so that custom cards (later discribed) will be shown properly.

### Pictures
Displays the Lights' status by placing all lighting images over the background depending on the lights' status (ON/OFF/unavailable).
Lights' images were created from the previously mentioned two main floorplan images.
The light images were named after the actual entity names.

### Weather
Displays a custom weather card for local weather status.

**Actions**
* Tap: Opens popup windows with hourly weather forecast.

  ![Weather](ScreenShots/weather_card_hourly_forecast.png?raw=true)

### Calendar
Displays a custom calendar card with upcoming events.

### Lights
#### Light Entity
Defines the lights' active areas where Tap Action will toggle lights.
These are transparent square images which are scaled (X,Y) as needed. The borders can be shown to help with the configuration.
The location and scale parametes are defined in and taken from the DEFINITIONS section.

![Lights](ScreenShots/lights.png?raw=true)

**Actions**
* Tap: Toggle light state
* Double Tap: Opens more-info popup window.

  ![Lights Double Tap Action](ScreenShots/light_double_tap_action.png?raw=true)

* Hold: Can be used for special lights (in my case popup windows of the amilight of the kitchen table light)

  ![Lights Tap Hold Action](ScreenShots/light_hold_action.png?raw=true)

#### Light Group
Defines the Light Group contol buttons.
If any of the lights in the group are unavailable the background color of the button will change to RED

![Lights Group](ScreenShots/light_group_warning.png?raw=true) ![Lights Group](ScreenShots/light_group.png?raw=true)

**Actions**
* Tap: Toggle all lights in that group.
* Double Tap: Opens a more-info popup window of the group.

  ![Lights Group Double Tap Action](ScreenShots/light_group_double_tap_action.png?raw=true)
* Hold: Popup window of all lights in the group

  ![Lights Group Hold Action](ScreenShots/light_group_hold_action.png?raw=true)

### Covers
#### Cover Entity
Defines the covers' active areas.
These are green/red/blue/grey square images (depending on the cover state) which are scaled (X,Y) as needed.
The location and scale parametes are defined in and taken from the DEFINITIONS section.

**Actions**
* Tap: According to what is defined in the DEFINITIONS section - usually toggle.
* Double Tap: Opens a more-info popup window of the group.

  ![Covers Double Tap Action](ScreenShots/cover_double_tap_action.png?raw=true)

* Hold: Popup window containing custom Vertical Slider Cover card of the Cover entity.

  ![Covers Tap Hold Action](ScreenShots/cover_hold_action.png?raw=true)

#### Cover Group
Defines the Cover Group contol buttons.
If any of the covers in the group are unavailable the background color of the button will change to RED.
The location parametes are defined in and taken from the DEFINITIONS section.

![Covers Group](ScreenShots/cover_group.png?raw=true)

**Actions**
* Tap: Open/Close/Stop all covers in that group depending which of the three buttons was presses
* Double Tap: Opens a more-info popup window of the group

  ![Covers Group Double Tap Action](ScreenShots/cover_group_double_tap_action.png?raw=true)
* Hold: Popup window with all covers in the group to control using the custom Vertical Slider Cover card

  ![Covers Group Hold Action](ScreenShots/cover_group_hold_action.png?raw=true)

### Irrigation
#### Irrigation Entity
Defines the Irrigation valves button location and groups.
If the irrigation valve is unavailable the background color of the button will change to RED.
The location parametes are defined in and taken from the DEFINITIONS section.

![Irrigation Button](ScreenShots/irrigation.png?raw=true)
![Irrigation Button 1 Scheduler](ScreenShots/irrigation_1_scheduler.png?raw=true)
![Irrigation Button 2 Schedulers](ScreenShots/irrigation_2_schedulers.png?raw=true)

**Actions**
* Tap: Toggles the valve (ON/OFF)
* Double Tap: Opens a more-info popup window

  ![Irrigation Double Tap Action](ScreenShots/irrigation_double_tap_action.png?raw=true)
* Hold: Opens the schedulers (2) for specific Irrigation Valve and includes:
  * Day of week
  * Enable/Disable the scheduler
  * Start Time
  * Duration

  ![Irrigation Hold Action](ScreenShots/irrigation_hold_action.png?raw=true)

#### Irrigation Group
Defines the Irrigation Group control buttons.
Show the total cycle time if a cycle is currently being run (cannot figure out how to show remaining time)
If any of the irrigation valves in the group are unavailable the background color of the button will change to RED

![Irrigation Group](ScreenShots/irrigation_group.png?raw=true)
![Irrigation Group](ScreenShots/irrigation_group_cycle.png?raw=true)
**Actions**
* Tap: Opens a popup window where you can run a 1-Time irrigation cycle
  * Choose which valves to include in cycle
  * Choose the duration of the cycle
  * Start/Stop the cycle
  * Show the remaining time of the current cycle
  * Shows the last 24 hour history of all irrigation valves in the group

  ![Irrigation Group Tap Action](ScreenShots/irrigation_group_tap_action.png?raw=true)
* Double Tap: Opens a more-info popup of the group

  ![Irrigation Group Double Tap Action](ScreenShots/irrigation_group_double_tap_action.png?raw=true)
* Hold: Opens Popup window with all irrigation valves in the group to control

  ![Irrigation Group Hold Action](ScreenShots/irrigation_group_hold_action.png?raw=true)

### Temperature Sensors
Displays all temperature sensors, depending on the Hide setting, that are defined in the relevant DEFINITIONS section - including their location on the floorplans

### Water Boiler
Defines the Water Boiler button location.
If the water boiler is unavailable the background color of the button will change to RED.
The location parametes are defined in and taken from the DEFINITIONS section.

![Water Boiler Button](ScreenShots/water_boiler.png?raw=true)
![Water Boiler 1 Scheduler](ScreenShots/water_boiler_1_scheduler.png?raw=true)
![Water Boiler 2 Schedulers](ScreenShots/water_boiler_2_schedulers.png?raw=true)
![Water Boiler Timer](ScreenShots/water_boiler_timer.png?raw=true)
![Water Boiler Timer Schedule](ScreenShots/water_boiler_timer_schedule.png?raw=true)

In addition gives history information regarding Water Boiler status and temperatures. The number of hours to show in the history graphs can be changed on-the-fly using the slider input.

![Water Boiler Information](ScreenShots/water_boiler_information.png?raw=true)

**Actions**
* Tap: Opens a popup window that includes:
  * Water Boiler button for direct control
  * 1-Time timer duration
  * Start time
  * Immediate timer start
  * Scheduled timer start (according to Start time)
  * Time left on timer

  ![Water Boiler Tap Action](ScreenShots/water_boiler_tap_action.png?raw=true)
* Double Tap: Opens a more-info popup window

  ![Water Boiler Double Tap Action](ScreenShots/irrigation_double_tap_action.png?raw=true)
* Hold: Opens the schedulers (2) for the Water Boiler that includes:
  * Day of week
  * Enable/Disable the scheduler
  * Start Time
  * Duration

  ![Water Boiler Hold Action](ScreenShots/irrigation_hold_action.png?raw=true)

### Vacuums
Defines the Vacuum Robots buttons' location.
If the Vacuum Robot is unavailable the background color of the button will change to RED.
The location parametes are defined in and taken from the DEFINITIONS section.

![Vacuum Button](ScreenShots/vacuum.png?raw=true)
![Vacuum 1 Scheduler](ScreenShots/vacuum_1_scheduler.png?raw=true)
![Vacuum 2 Schedulers](ScreenShots/vacuum_2_schedulers.png?raw=true)

**Actions**
* Tap: Opens a popup window that includes:
  * Control of the vacuum - Custom Vacuum Card
  * Vacuum Map - Xiaomi Cloud Map Extractor integration

  ![Vacuum Tap Action](ScreenShots/vacuum_tap_action.png?raw=true)
* Double Tap: Opens a more-info popup window

  ![Vacuum Double Tap Action](ScreenShots/vacuum_double_tap_action.png?raw=true)
* Hold: Opens the schedulers (2) for the Vacuum that includes:
  * Day of week
  * Enable/Disable the scheduler
  * Start Time

  ![Vacuum Hold Action](ScreenShots/vacuum_hold_action.png?raw=true)

### Media Players
TBD

### HVAC
Defines the HVAC buttons' location.
If the HVAC control is unavailable the background color of the button will change to RED.
The temperature of the HVAC set point device is shown and also the HVAC set temperature, mode and fan speed if the HVAC is ON.
The location parametes are defined in and taken from the DEFINITIONS section.

![HVAC Button](ScreenShots/hvac.png?raw=true)
![HVAC 1 Scheduler](ScreenShots/hvac_1_scheduler.png?raw=true)
![HVAC 2 Schedulers](ScreenShots/hvac_2_schedulers.png?raw=true)
![HVAC 3 Schedulers](ScreenShots/hvac_3_schedulers.png?raw=true)
![HVAC 4 Schedulers](ScreenShots/hvac_4_schedulers.png?raw=true)
![HVAC ON](ScreenShots/hvac_on.png?raw=true)

**Actions**
* Tap: Opens a popup window to control the HVAC using Thermostat Card

  ![HVAC Tap Action](ScreenShots/hvac_tap_action.png?raw=true)
* Double Tap: Opens a more-info popup window

  ![HVAC Double Tap Action](ScreenShots/hvac_double_tap_action.png?raw=true)
* Hold: Opens the schedulers (4) for the HVAC that includes:
  * Enable/Disable the scheduler
  * Temperature set point
  * Mode (OFF/HEAT/COOL/AUTO)
  * Fan Speed (Low/Medium/High)
  * Start Time - To stop the HVAC just set a scheduler to mode OFF and set the start time as the stop time you want

  ![HVAC Hold Action](ScreenShots/hvac_hold_action.png?raw=true)

### Navigation
Displays the Waze Navigation routes, icons and time to destination.
The list of entities and look&feel is defined and taken from the DEFINITIONS section.

### Status Bar
Creates and populizes the Status Bar.

![Status Bar](ScreenShots/status_bar.png?raw=true)

The entities to show are defined and taken from the DEFINITIONS section.
**Actions:**
* Tap: Opens a popup window that shows relevant entities defined in the DEFINITIONS section
  
  ![Status Bar Tap Action Example 1](ScreenShots/status_bar_tap_action_1.png?raw=true) ![Status Bar Tap Action Example 2](ScreenShots/status_bar_tap_action_2.png?raw=true) ![Status Bar Tap Action Example 3](ScreenShots/status_bar_tap_action_3.png?raw=true)
* Hold: Opens a more-info popup window

  ![Status Bar Hold Action Example 1](ScreenShots/status_bar_hold_action_1.png?raw=true) ![Status Bar Hold Action Example 2](ScreenShots/status_bar_hold_action_2.png?raw=true) ![Status Bar Hold Action Example 3](ScreenShots/status_bar_hold_action_3.png?raw=true)

### Settings
Creates and populizes the Settings popup window.

![Settings](ScreenShots/settings.png?raw=true)

The entities to show are defined and taken from the DEFINITIONS section.
The settings page is divided into columns. Each column can have multiple sections. Each section can have multiple entities.
**Actions:**
* Tap: Opens a popup window that shows relevant settings entities defined in the DEFINITIONS section
  ![Settings Tap Action](ScreenShots/settings_tap_action.png?raw=true)

### UnRaid
TBD

### Water
Displays water consumption data in graphs

![Water](ScreenShots/water.png?raw=true)

**Actions:**
* Tap: Opens popup window with all relevant history information using relevant integration entities.

### Actions
Buttons for special/quick access funcitons/scenarios
The look&feel and list of Actions are defined in and taken from the DEFINITIONS section.

![Actions](ScreenShots/actions.png?raw=true)

**Actions:**
* Tap: Active toggle
* Double Tap: Opens a more-info popup window
* Hold: Opens a more-info popup window

### Conditional Entity
TBD

### Refresh Reload
Buttons for refreshing/reloading UI

![Refresh/Reload](ScreenShots/refresh_reload.png?raw=true)

**Actions:**
* Tap: UI refresh
* Double Tap: Browser window refresh/reload

## Sources
### Integrations
[browser_mod](https://github.com/thomasloven/hass-browser_mod) * 
[City-Mind Water Meter](https://github.com/maorcc/citymind_water_meter) * 
[lovelace_gen](https://github.com/thomasloven/hass-lovelace_gen) * 
[Xiaomi Cloud Map Extractor](https://github.com/PiotrMachowski/Home-Assistant-custom-components-Xiaomi-Cloud-Map-Extractor)

### Custom Cards
[Atomic Calendar Revive](https://github.com/marksie1988/atomic-calendar-revive) * 
[Config Template Card](https://github.com/iantrich/config-template-card) * 
[Lovelace Slider Entity Row](https://github.com/thomasloven/lovelace-slider-entity-row) * 
[Lovelace Time Picker Card](https://github.com/GeorgeSG/lovelace-time-picker-card) * 
[Lovelace Vertical Slider Cover Card](https://github.com/konnectedvn/lovelace-vertical-slider-cover-card) * 
[Mini Media Player](https://github.com/kalkih/mini-media-player) * 
[Simple Thermostat](https://github.com/nervetattoo/simple-thermostat) * 
[Vacuum Card](https://github.com/denysdovhan/vacuum-card) * 
[Weather Card](https://github.com/bramkragten/weather-card)

## Support
<a href="https://www.buymeacoffee.com/dankessler" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/white_img.png" alt="Buy Me A Beer" style="height: auto !important;width: auto !important;" ></a>
