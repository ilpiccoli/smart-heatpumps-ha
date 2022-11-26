In order to correctly use those automations you will need to have these sensors in your HomeAssistant istance.
Not all of them are necessary but you will need to manually remove them from automations etc.
If you want to use those automations in the most "plug and play" way i suggest you to name them in the same way as i did, in this way the automations will be already done and ready to work

## Sensors
- *sensor.meter_reading_filtered* : a filtered sensor based on your meter reading sensor
- The ones in *binary_sensors.yaml* file

## Timers
- *timer.start_self_consumption*
- *timer.stop_self_consumption*
- *timer.wait_time_start_heatpump*

## Groups
- *group.family* : a group with device tracker to decide whether someone is home or not
- *group.heatpumps* : a group with all heatpumps

## Binary sensors
- Those described in *binary_sensors.yaml* file

## Input booleans
- *input_boolean.auto_heatpumps* : to quickly enable/disable and start the automation from lovelace frontend
