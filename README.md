# domoticz_bmv

## ap_bmv.lua
Lua script to parse json data to domoticz devices via their IDs

### Installation
* Install to your Domoticz folder i.e. /domoticz/scripts/lua_parsers
* Create a BMV parser hardware type 'Dummy' in Domoticz
* Create BMV devices in Domoticz using 'Create Virtual Sensors' button in the Dummy hardware
Example: BMV Volts, BMV Amps, BMV Power, BMV SOC, BMV AHr
* Go to the Devices page and filter for 'BMV' to make them easier to spot.
* Note the Domoticz index (Idx) for each device and update ap_bmv.lua for each item in the array.

This script is triggered by a URL generated in the python script vedirect.py (see below).  When the BMV python script sends a command to Domoticz, formatted as a JSON URL, this Lua script intercepts and parses the values to Domoticz. The values may be corrected with multipliers.

If you rename this script, change the name also in the python calling script. i.e. vedirect.py.

## vedirect.py
Version 2.0, Python 3

Send Victron BMV (702) values to Domoticz as JSON and/or optionally log to CSV data file.

Example URL: http://domoticz_domain_orIP#:port#/json.htm?type=command&param=udevices&script=ap_bmv.lua&data={"H2":0,"H3":0,"Alarm":"OFF","H7":46666,"V":54645,"FW":307,"H10":14,"H4":0,"H8":60004,"H11":0,"H12":0,"SOC":1000,"H1":-170364,"AR":0,"BMV":700,"CE":0,"P":29,"Relay":"OFF","I":530,"PID":"0x203","TTG":-1,"H9":0,"H17":26572,"H5":0,"H18":41698,"H6":-7695869}

Adapted from various versions of vedirect.py, particularly https://github.com/karioja/vedirect/blob/master/vedirect.py

### Installation
* Install in your chosen folder i.e. /monitor/bmv/vedirect.py
* Set up to run at system startup.
Example: create /lib/systemd/system/ap_bmv.service

[Unit]
Description=Victron BMV logging service
After=multi-user.target

[Service]
Type=idle
ExecStart=/usr/bin/python3 /home/pi/monitor/bmv/vedirect.py

[Install]
WantedBy=multi-user.target
