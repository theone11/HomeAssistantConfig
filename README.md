- [HomeAssistantConfig](#homeassistantconfig)
  - [UI Explained](#ui-explained)
    - [Definition](#definition)
    - [Macros](#macros)
    - [Start](#start)
    - [Pictures](#pictures)
    - [Weather Card](#weather-card)
    - [Calendar Card](#calendar-card)
    - [Lights](#lights)
      - [Light Entity](#light-entity)
      - [Light Group](#light-group)
    - [Covers](#covers)
      - [Cover Entity](#cover-entity)
      - [Cover Group](#cover-group)
    - [Irrigation](#irrigation)
      - [Irrigation Entity](#irrigation-entity)
      - [Irrigation Group](#irrigation-group)
    - [Water Boiler](#water-boiler)
  - [Sources](#sources)
    - [Integrations](#integrations)
    - [Custom Cards](#custom-cards)

# HomeAssistantConfig

This is my HomeAssistant configuration.

The main goal was to have the day-to-day activations and information always available/visible and everything else (like schedulers, history graphs) available upto 1-click away.

My main interface with the systen is via two wall mounted DIY 15.6 RaspberryPi based touchscreens. One on each floor.

You can take a glance at the functionality here (although not up-to-date):

[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/o_AKHEyWXR0/0.jpg)](https://www.youtube.com/watch?v=o_AKHEyWXR0)

The main goal was to have the day-2-day activations and information always available/visible and everything else (like schedulers, history graphs) available upto 1-click away.

The UI is defined in the *lovelace_new_data.yaml* file.
Each section has a header and implements a different part of the UI.

All house images were created using SweetHome3D software and manipulated using GIMP image editing SW.

Two main floorplan images are the starting point:
* All lights OFF
* All light ON

Only custom cards can be displayed on the UI so if an internal HA card need to be shown then a custom card template should be used as wrapper.

## UI Explained
<a name="definitions"/>

<a name="definitions"/>

### Definition
Contains parameters and settings for the UI to easily change the look-and-feel of the UI.

<a name="macros"/>

### Macros
Contains "functions" to simplify reoccuring UI elements.

<a name="start"/>

### Start
Defines the background image of the house with transparecny in all areas outside the floorplan boundaries so that custom cards (later discribed) will be shown properly.

<a name="pictures"/>

### Pictures
Displays the Lights' status by placing all lighting images over the background depending on the lights' status (ON/OFF/unavailable).

Lights' images were created from the previously mentioned two main floorplan images.

The light images were named after the actual entity names.

<a name="weather_card"/>

### Weather Card
Displays a custom weather card for local weather status.

Tap Action on the weather card will open up the hourly weather forecast.

![Weather Card](ScreenShots/weather_card_hourly_forecast.png?raw=true)

<a name="calendar_card"/>

### Calendar Card
Displays a custom calendar card with upcoming events.

<a name="lights"/>

### Lights
#### Light Entity
Defines the lights' active areas where Tap Action will toggle lights.
These are transparent square images which are scaled (X,Y) as needed. The borders can be shown to help with the configuration.

The location and scale parametes are defined in and taken from the DEFINITIONS section.

![Lights](ScreenShots/lights.png?raw=true)

Double Tap Action will open a more-info popup window.

![Lights Double Tap Action](ScreenShots/light_double_tap_action.png?raw=true)

Hold Action can be used for special lights (in my case the amilight of the kitchen table light)

![Lights Tap Hold Action](ScreenShots/light_hold_action.png?raw=true)

#### Light Group
Defines the Light Group contol buttons.

![Lights Group](ScreenShots/light_group.png?raw=true)

If any of the lights in the group are unavailable the background color of the button will change to RED

![Lights Group](ScreenShots/light_group_warning.png?raw=true)
* Tap Action will toggle all lights in that group.
* Double Tap Action will give more-info of the group.

![Lights Group Double Tap Action](ScreenShots/light_group_double_tap_action.png?raw=true)
* Hold Action will display a popup window with all lights in the group to control.

![Lights Group Hold Action](ScreenShots/light_group_hold_action.png?raw=true)

<a name="covers"/>

### Covers
<a name="cover_entity"/>

#### Cover Entity
Defines the covers' active areas where Tap Action will open/close/stop covers.
These are green/red/blue/grey square images (depending on the cover state) which are scaled (X,Y) as needed.

The location and scale parametes are defined in and taken from the DEFINITIONS section.

Double Tap Action will open a more-info popup window.

![Covers Double Tap Action](ScreenShots/cover_double_tap_action.png?raw=true)

Hold Action is used to display the custom Vertical Slider Cover card.

![Covers Tap Hold Action](ScreenShots/cover_hold_action.png?raw=true)

<a name="cover_group"/>

#### Cover Group
Defines the Cover Group contol buttons.

![Covers Group](ScreenShots/cover_group.png?raw=true)

If any of the covers in the group are unavailable the background color of the button will change to RED

* Tap Action will open/close/stop all lights in that group depending which of the three buttons was presses.
* Double Tap Action will give more-info of the group.

![Covers Group Double Tap Action](ScreenShots/cover_group_double_tap_action.png?raw=true)
* Hold Action will display a popup window with all covers in the group to control using the custom Vertical Slider Cover card.

![Covers Group Hold Action](ScreenShots/cover_group_hold_action.png?raw=true)

<a name="irrigation"/>

### Irrigation
<a name="irrigation_entity"/>

#### Irrigation Entity
Defines the Irrigation valves button location and groups.

The location parametes are defined in and taken from the DEFINITIONS section.

![Irrigation Button](ScreenShots/irrigation.png?raw=true)
![Irrigation Button 1 Scheduler](ScreenShots/irrigation_1_scheduler.png?raw=true)
![Irrigation Button 2 Schedulers](ScreenShots/irrigation_2_schedulers.png?raw=true)

* Actions
  * Tap: Toggles the valve (ON/OFF)
  * Double Tap: Opens the more-info popup window.

![Irrigation Double Tap Action](ScreenShots/irrigation_double_tap_action.png?raw=true)

* Hold: Opens the schedulers (2) for specific Irrigation Valve and includes:
  * Day of week
  * Enable/Disable the scheduler
  * Start Time
  * Duration

![Irrigation Double Tap Action](ScreenShots/irrigation_hold_action.png?raw=true)

<a name="irrigation_group"/>

#### Irrigation Group
Defines the Irrigation Group control buttons.

![Irrigation Group](ScreenShots/irrigation_group.png?raw=true)

Show the total cycle time if a cycle is currently being run (cannot figure out how to show remaining time)

![Irrigation Group](ScreenShots/irrigation_group_cycle.png?raw=true)

If any of the irrigation valves in the group are unavailable the background color of the button will change to RED
* Actions:
  * Tap: Opens a popup window where you can run a 1-Time irrigation cycle
    * Choose which valves to include in cycle.
    * Choose the duration of the cycle.
    * Start/Stop the cycle.
    * Show the remaining time of the current cycle
    * Shows the 24 hour history of all irrigation valves in the group

    ![Irrigation Group Tap Action](ScreenShots/irrigation_group_tap_action.png?raw=true)
  * Double Tap: Opens more-info popup of the group.

    ![Irrigation Group Double Tap Action](ScreenShots/irrigation_group_double_tap_action.png?raw=true)
  * Hold: Opens Popup window with all irrigation valves in the group to control.

    ![Irrigation Group Hold Action](ScreenShots/irrigation_group_hold_action.png?raw=true)

### Water Boiler
<a name="water_boiler"/>
Defines the Water Boiler button location.

The location parametes are defined in and taken from the DEFINITIONS section.

![Water Boiler Button](ScreenShots/water_boiler.png?raw=true)
![Water Boiler 1 Scheduler](ScreenShots/water_boiler_1_scheduler.png?raw=true)
![Water Boiler 2 Schedulers](ScreenShots/water_boiler_2_schedulers.png?raw=true)
![Water Boiler Timer](ScreenShots/water_boiler_timer.png?raw=true)
![Water Boiler Timer Schedule](ScreenShots/water_boiler_timer_scheduler.png?raw=true)

* Actions
  * Tap: Opens a popup window where you can run a 1-Time Water Boiler timer
    * Water Boiler button for direct control
    * Timer duration
    * Start time
    * Immediate timer start
    * Scheduled timer start (according to Start time)
    * Time left on timer

    ![Water Boiler Tap Action](ScreenShots/water_boiler_tap_action.png?raw=true)
  * Double Tap: Opens the more-info popup window.

    ![Irrigation Double Tap Action](ScreenShots/irrigation_double_tap_action.png?raw=true)
  * Hold: Opens the schedulers (2) for the Water Boiler and includes:
    * Day of week
    * Enable/Disable the scheduler
    * Start Time
    * Duration

    ![Irrigation Double Tap Action](ScreenShots/irrigation_hold_action.png?raw=true)

## Sources
<a name="sources"/>

### Integrations
<a name="integrations"/>

[browser_mod](https://github.com/thomasloven/hass-browser_mod)

[lovelace_gen](https://github.com/thomasloven/hass-lovelace_gen)

### Custom Cards
<a name="custom_cards"/>

[Atomic Calendar Revive](https://github.com/marksie1988/atomic-calendar-revive)

[Config Template Card](https://github.com/iantrich/config-template-card)

[Lovelace Slider Entity Row](https://github.com/thomasloven/lovelace-slider-entity-row)

[Lovelace Time Picker Card](https://github.com/GeorgeSG/lovelace-time-picker-card)

[Lovelace Vertical Slider Cover Card](https://github.com/konnectedvn/lovelace-vertical-slider-cover-card)

[Mini Media Player](https://github.com/kalkih/mini-media-player)

[Simple Thermostat](https://github.com/nervetattoo/simple-thermostat)

[Vacuum Card](https://github.com/denysdovhan/vacuum-card)

[Weather Card](https://github.com/bramkragten/weather-card)



