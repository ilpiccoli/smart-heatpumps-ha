# Smart Heatpumps HA (HomeAssistant)

This github repository will be regularly updated based on my tests and is made based on my specific home setup.
I tried to write that in the most explanatory way so that it will be simple for anyone to adapt it to their needings.
I hope it will help other people in the same situation as mine.

Any hint, suggestion or comment on the [Discussion](https://github.com/ilpiccoli/smart-heatpumps-ha/discussions) page is really appreciated.

If you want to support me you can [buy me a coffee](https://www.buymeacoffee.com/ilpiccoli).

## How to install
Check if you satisfy all the pre-requisites in the [related](https://github.com/ilpiccoli/smart-heatpumps-ha/blob/main/pre-requisites.md) page

Follow the instructions on the [How to install](https://github.com/ilpiccoli/smart-heatpumps-ha/blob/main/how_to_install.md) file

## What's the purpose of this repository?
I have 5 Daikin splits (1 Emura and 4 FTXM35N) and 2 motors (2MXM50M and 2MXM25M, respectively controlling 3 and 2 internal units) and a 4.14kWp photovoltaic system: the goal was to exploit as much solar power as i can to avoid using my radiators (or at least reduce their consumption) and so save money.

You can find the data and *statistics* i learned during my tests in the [related page](https://github.com/ilpiccoli/smart-heatpumps-ha/blob/main/some_numbers.md)

## How to connect HVAC to HomeAssistant?
I am using the [official Daikin integration](https://www.home-assistant.io/integrations/daikin/) and their exposed sensor: i can set temperature, hvac mode, fan mode, swing mode, preset mode, consumption of every internal unit and every motor and internal temperature of every room.

To improve accuracy i use external sensors to retrieve rooms' temperatures, in particular i use temperature attributes exposed from my Tado° and Netatmo thermostats and two Sonoff Zigbee Temperature and Humidity sensors connected to a Tasmota flashed Sonoff Zigbee Bridge

## How does it work
Note: when i write *meter reading* or *power consumption* i mean what the grid meter sees, so it is the result of actual consumption minus solar panels production.

Note pt2: All the automation are set to work only between sunrise and sunset, to avoid unnecessary heatpumps stops when manually turning them on by evening

The idea behind this set of automation is to run heatpumps "for free", mantaining my base consumption and using solar production to power them.
I'll explain: i have a base consumption of ~700W by night, so i know that's my base consumption. As my heatpumps consume ~200W i set the automations to start when the meter reading (actual consumption - solar production) is below 325W, so that i can *buy* at maximum 700W, as i did not have any solar panel.

##### When any of these trigger is satisfied the automation **tries** to start:
- Power consumption is below 325W in the last 5 minutes (so *binary_sensor.start_heatpumps* is ON)
- Power consumption is below 1000W in the last 15 minutes (so *binary_sensor.stop_heatpumps_consumption* is OFF : that was made to let the heatpumps restart after a stop, for example a dishwasher starting, cooking with induction hob etc)
- 10 minutes have passed since last heatpump started (so *timer.wait_time_start_heatpump* has finished : that was made to avoid starting more heatpumps simultaneously, to reduce false positive from peak start consumption)
- The automation was turned on (so *input_boolean.auto_heatpumps* is ON : that was made both to start immediately the automation if conditions are satisfied and to use this as a test trigger when changing some parameters in the yaml files)
- Every 15 minutes, in any case

#### If the automation was triggered, it checks if those conditions are satisfied:
- Automation needs to be ON
- *binary_sensor.start_heatpumps* needs to be ON (meaning that we have enough power to start heatpumps)
- Automation stop needs to be OFF (*binary_sensor.stop_heatpumps_consumption*, it means we haven't had a peak consumption, above 1000W, in the last 15 minutes)
- Power consumption is below 600W, so we still have margin to start another heatpump staying under 700W
- Someone was home in the last 12 hours (so *binary_sensor.away_mode_heatpumps* is OFF : that was made because it has no sense to warm the house during holiday times, this means that we need to manually turn heating on when returning home, the binary sensor turns back ON as soon as the first person enter the house zone)

#### Now that the automation was triggered and conditions are satisfied, we can start the automation:
It checks from *sensor.heatpump_to_start* which is the coldest room with HVAC off (to avoid starting again HVAC in a room still being warmed) and, if the temperature in that room is below threshold, it refers to its specifical script file, in which there are specific instructions for that HVAC (in my case goal temperature, desidered fan mode, ECO mode to avoid starting peak consumption, turning off thermostat scheduling to reduce gas consumptions, sending telegram notification etc).
A 10 minutes timer is started, after which it will check again if conditions are satisfied and eventually turn on another heatpump (if no other triggers are triggered before)

#### When will the heatpumps stop?
There are various scenarios in which one (or all) the heatpumps are stopped:
- If power consumption is above 325W for 6 hours (so for example by night or during cloudy days) all are shutted off
- If above 700W for 15 minutes, it will stop the HVAC in the warmest room between the rooms with HVAC on, same if above 1000W for 3 minutes, to try reduce power consumption without sacrifying comfort
- If above 700W for 45 minutes all are shutted off
- If above 1400W for 3 minutes all are shutted off
- If a specific room reaches a "too hot" temperature it is stopped, this paramater is specifically set in its *auto_heatpumps_single.yaml* file (e.g. when above 19°C)

