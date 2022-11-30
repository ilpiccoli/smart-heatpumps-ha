# How to install
Check if you satisfy all the pre-requisites in the [related](https://github.com/ilpiccoli/smart-heatpumps-ha/blob/main/pre-requisites.md) page

To install the "program" you simply need to copy the files in the folder [*Smart Heatpumps HA*](https://github.com/ilpiccoli/smart-heatpumps-ha/tree/main/Smart%20Heatpumps%20HA) in this way:

## Automations
You need to copy those files into your *automations* folder or copy their content into your `automations.yaml` file or copy it under the *automations:* part in your `configuration.yaml` file:
- `auto_heatpumps_main.yaml` : Here there are all the main automations
- `auto_heatpump_single.yaml` : You can copy and rename this file for each heat pump you have, this is an extra file if you want to set specific conditions to turn off a single heat pump (in my case when the temperature in that specific room is too high)

## Scripts
You need to copy this file into your *scripts* folder or copy its content into your `scripts.yaml` file or copy it under the *scripts:* part in your `scripts.yaml` file:
- `scripts.yaml` : Here it is set all the scripts to turn on or off the heat pumps

## Binary sensors
You need to copy this file into your *binary_sensor* folder or copy its content into your `binary_sensor.yaml` file or copy it under the *sensor:* part in your `configuration.yaml` file:
- `binary_sensor.yaml` : Here are stored the two binary sensor to know which is the coldest HVAC stil to be turned on and the warmest to be turned off

## Sensors
You need to copy this file into your *sensors* folder or copy its content into your `sensors.yaml` file or copy it under the *sensor:* part in your configuration.yaml` file:
- `template_sensors.yaml` : Here are stored the two sensors to know which HVAC is the next to be started and which the next to be stopped

If you have any doubt on where to copy those files double check on [HomeAssistant official website](https://www.home-assistant.io)
