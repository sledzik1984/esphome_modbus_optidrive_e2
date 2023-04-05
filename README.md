# esphome_modbus_optidrive_e2
ESPHome YAML Configuration for MODBUS communication with Intvertek Optidrive E2

After uploading this to your ESPHOME board (I am using ESP32) you will be able to:
 - read some parameters by MODBUS from Optidrive E2 (like: actual running frequency, current driving the motor, device temperature)
 - set some parameters by MODBUS (like: start the motor, set RAMP time, set output frequency, reset drive faults, etc.)
 
 
 To add more parameters you have to remember that all Modbus registers have offset by -1 register (so register 7 in docs is register 6 in ESPHOME Yaml)
 
 Parameters set by keyboard in Optidrive E2:
 
 P12: 4 (Modbus Network Control. Control via Modbus RTU (RS485) interface with Accel / Decel ramps updated via Modbus) - remember that if you set that parameter to 4
 you have to set RAMP time. If RAMP time is set to 0s drive will start only on low frequencies. Starting my drive with output freq set to 30Hz will stop the drive as 
 the current going through is too high
 
 P36:
  - Baud rate: 9600
  - Address - set as needed (and change in Yaml)
  - Watchdog timeout: 0 (set as needed AFTER reading Invertek docs)
  
Please remember that motor inverters (like Optidrive E) are dangereous devices and you should not touch it if you have no knowledge about electricity (and of course if 
you have no "electrician permission" needed in your country.

YOU HAVE BEEN WARNED!
