# HomeAssistantConfig

This is my HomeAssistant configuration.

The main goal was to have the day-to-day activations and information always available/visible and everything else (like schedulers, history graphs) available upto 1-click away.

My main interface with the systen is via two wall mounted DIY 15.6 RaspberryPi based touchscreens. One on each floor.

You can take a glance at the functionality here (although not up-to-date):

![Youtube](https://www.youtube.com/watch?v=o_AKHEyWXR0)

The main goal was to have the day-2-day activations and information always available/visible and everything else (like schedulers, history graphs) available upto 1-click away.

The UI is defined in the *lovelace_new_data.yaml* file.
Each section has a header and implements a different part of the UI.

All house images were created using SweetHome3D software and manipulated using GIMP image editing SW.

Two main floorplan images are the starting point:
* All lights OFF
* All light ON

Only custom cards can be displayed on the UI so if an internal HA card need to be shown then a custom card template should be used as wrapper.

## Table of Contents
[Definitions](#definitions)
[Macros](#macros)
[Start](#start)
[Pictures](#pictures)
[Weather Card](#weather_card)
[Calendar Card](#calendar_card)
[Lights](#lights)
[Cover](#covers)
[Irrigation Group](#irrigation_group)

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

![Alt text](ScreenShots/weather_card_hourly_forecast.png?raw=true "Weather Card")

<a name="calendar_card"/>

### Calendar Card
Displays a custom calendar card with upcoming events.

<a name="lights"/>

### Lights
Defines the lights' active areas where Tap Action will toggle lights.
These are transparent square images which are scaled (X,Y) as needed. The borders can be shown to help with the configuration.

The location and scale parametes are defined in and taken from the DEFINITIONS section.

![Alt text](ScreenShots/lights.png?raw=true "Lights")

Double Tap Action will open a more-info popup window.

![Alt text](ScreenShots/light_double_tap_action.png?raw=true "Lights Double Tap Action")

Hold Action can be used for special lights (in my case the amilight of the kitchen table light)

![Alt text](ScreenShots/light_hold_action.png?raw=true "Lights Tap Hold Action")


This section also defines the Light Group contol buttons.

![Alt text](ScreenShots/light_group.png?raw=true "Lights Group")

* Tap Action will toggle all lights in that group.
* Double Tap Action will give more-info of the group.

![Alt text](ScreenShots/light_group_double_tap_action.png?raw=true "Lights Group Double Tap Action")
* Hold Action will display a popup window with all lights in the group to control.

![Alt text](ScreenShots/light_group_hold_action.png?raw=true "Lights Group Hold Action")

<a name="covers"/>

### Covers
Defines the covers' active areas where Tap Action will open/close/stop covers.
These are green/red/blue/grey square images (depending on the cover state) which are scaled (X,Y) as needed.

The location and scale parametes are defined in and taken from the DEFINITIONS section.

Double Tap Action will open a more-info popup window.

![Covers Double Tap Action](ScreenShots/cover_double_tap_action.png?raw=true)

Hold Action is used to display the custom Vertical Slider Cover card.

![Covers Tap Hold Action](ScreenShots/cover_hold_action.png?raw=true)

This section also defines the Cover Group contol buttons.

![Covers Group](ScreenShots/cover_group.png?raw=true)
* Tap Action will open/close/stop all lights in that group depending which of the three buttons was presses.
* Double Tap Action will give more-info of the group.

![Covers Group Double Tap Action](ScreenShots/cover_group_double_tap_action.png?raw=true)
* Hold Action will display a popup window with all covers in the group to control using the custom Vertical Slider Cover card.

![Covers Group Hold Action](ScreenShots/cover_group_hold_action.png?raw=true)

<a name="irrigation_group"/>

### Irrigation Group

Defines the Irrigation Group control buttons.

![Irrigation Group](ScreenShots/irrigation_group.png?raw=true)

Show the total cycle time if a cycle is currently being run (cannot figure out how to show remaining time)

![Irrigation Group](ScreenShots/irrigation_group_cycle.png?raw=true)
* Tap Action will open a popup window where you can run a 1-Time irrigation cycle
  * Choose which valves to include in cycle.
  * Choose the duration of the cycle.
  * Start/Stop the cycle.
  * Show the remaining time of the current cycle
  * Shows the 24 hour history of all irrigation valves in the group

![Irrigation Group Tap Action](ScreenShots/irrigation_group_tap_action.png?raw=true)
* Double Tap Action will give more-info of the group.

![Irrigation Group Double Tap Action](ScreenShots/irrigation_group_double_tap_action.png?raw=true)
* Hold Action will display a popup window with all irrigation valves in the group to control.

![Irrigation Group Hold Action](ScreenShots/irrigation_group_hold_action.png?raw=true)

