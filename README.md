# Smart Heatpumps HA (HomeAssistant)

## Intro
This github repository is actually a **WORK IN PROGRESS**, it will be regularly updated based on my tests and is made based on my specific home setup.
I hope it will help other people in the same situation as mine.

Any hint, suggestion or comment on the *Discussion* page is really appreciated.

You can also follow the updates from the community on the official HomeAssistant forum here: [Forum Discussion](https://community.home-assistant.io/t/transform-my-heatpumps-into-smart-heatpumps-with-solar/488002)

If you want to support me you can [buy me a coffee](https://www.buymeacoffee.com/ilpiccoli).

## Setup and needings
I have 5 Daikin splits (1 Emura and 4 FTXM35N) and 2 motors (2MXM50M and 2MXM25M, respectively controlling 3 and 2 internal units) and a 4.14kWp photovoltaic system: the goal would be to exploit as much as i can the power from the solar panels to avoid using my radiators and so save money.

You can find the data and *statistics* i learned during my tests in the [related page](https://github.com/ilpiccoli/smart-heatpumps-ha/blob/main/some_numbers.md)

## Sensors exposed and needed
I am using the [official Daikin integration](https://www.home-assistant.io/integrations/daikin/) and their exposed sensor: i can set temperature, hvac mode, fan mode, swing mode, preset mode, consumption of every internal unit and every motor and internal temperature of every room (even if i use external sensor to improve accuracy)

## Code written by now and logic behind the automations
You can find the idea behind every code i wrote in the [roadmap page](https://github.com/ilpiccoli/smart-heatpumps-ha/blob/main/roadmap.md)

