# HomeAssistantConfig

This is my HomeAssistant configuration.

The main goal was to have the day-to-day activations and information always available/visible and everything else (like schedulers, history graphs) available upto 1-click away.

My main interface with the systen is via two wall mounted DIY 15.6 RaspberryPi based touchscreens. One on each floor.

You can take a glance at the functionality here (although not up-to-date):
[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/o_AKHEyWXR0/0.jpg)](https://www.youtube.com/watch?v=o_AKHEyWXR0)

The main goal was to have the day-2-day activations and information always available/visible and everything else (like schedulers, history graphs) available upto 1-click away.

## Changing the UI configuration

The UI is defined in the *lovelace_new_data.yaml* file.
Each section has a header and implements a different part of the UI.

All house images were created using SweetHome3D software and manipulated using GIMP image editing SW.
Two main floorplan images are the starting point:
* All lights OFF
* All light ON

Only custom cards can be displayed on the UI so if an internal HA card need to be shown then a custom card template should be used as wrapper.

### Definition
Contains parameters and settings for the UI to easily change the data shown and the look-and-feel of the UI.

### Macros
Contains "functions" to simplify reoccuring UI elements.

### Start
Defines the background image of the house with transparecny in all areas outside the floorplan boundaries so that custom cards (later discribed) will be shown properly.

### Pictures
Displays the Lights' status by placing all lighting images over the background depending on the lights' status (ON/OFF/unavailable).
Lights' images were created from the previously mentioned two main floorplan images.
The light images were named after the actual entity names.

### Weather Card
Displays a custom weather card for local weather status.
Clicking on the weather card will open up the hourly weather forcast.
![Alt text](ScreenShots/weather_card_hourly_forecast.png?raw=true "Weather Card")

### Calendar Card

