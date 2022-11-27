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
I have 5 Daikin splits (1 Emura and 4 FTXM35N) and 2 motors (2MXM50M and 2MXM25M, respectively controlling 3 and 2 internal units) and a 4.14kWp photovoltaic system: the goal would be to exploit as much as i can the power from the solar panels to avoid using my radiators and so save money.

You can find the data and *statistics* i learned during my tests in the [related page](https://github.com/ilpiccoli/smart-heatpumps-ha/blob/main/some_numbers.md)

## How to connect HVAC to HomeAssistant?
I am using the [official Daikin integration](https://www.home-assistant.io/integrations/daikin/) and their exposed sensor: i can set temperature, hvac mode, fan mode, swing mode, preset mode, consumption of every internal unit and every motor and internal temperature of every room.

To improve accuracy i use external sensors to retrieve rooms' temperatures, in particular i use temperature attributes exposed from my Tado° and Netatmo thermostats and two Sonoff Zigbee Temperature and Humidity sensors connected to a Tasmota flashed Sonoff Zigbee Bridge

## How does it work
Still to be written, sorry

