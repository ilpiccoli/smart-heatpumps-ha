# Version 1.0 - November 2022

The automations are working! I am using my HVAC "for free" exploiting electricity from my solar panels but there's still much work to do...

## Sensors
I created the following sensors:

- **Binary sensors**
    - Power Availability from the Photovoltaic System (*binary_sensor.disponibilita_pdc*): it is on when the meter reading is below -350W for 15 minutes
    - Power Consumption is too high (*binary_sensor.stop_pdc_consumi*): it is on when the meter reading is above 700W for 10 minutes
