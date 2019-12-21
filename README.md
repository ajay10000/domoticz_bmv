# domoticz_bmv

## ap_bmv.lua
Lua script to parse json data to domoticz devices via their IDs

Install to your Domoticz folder i.e. domoticz/scripts/lua_parsers

Called by url generated in python script vedirect.py (see below)

When the BMV python script sends a JSON command to Domoticz, this script intercepts and parses the values to Domoticz. The values may be corrected with multipliers.

If you rename this script, change the name also in the python calling script. i.e. vedirect.py.

## vedirect.py
Version 2.0, Python 3

Send Victron BMV (702) values to Domoticz as JSON and/or optionally log to CSV data file.

Example: http://domoticz_domain_orIP#:port#/json.htm?type=command&param=udevices&script=ap_bmv.lua&data={"H2":0,"H3":0,"Alarm":"OFF","H7":46666,"V":54645,"FW":307,"H10":14,"H4":0,"H8":60004,"H11":0,"H12":0,"SOC":1000,"H1":-170364,"AR":0,"BMV":700,"CE":0,"P":29,"Relay":"OFF","I":530,"PID":"0x203","TTG":-1,"H9":0,"H17":26572,"H5":0,"H18":41698,"H6":-7695869}

Adapted from various versions of vedirect.py, particularly https://github.com/karioja/vedirect/blob/master/vedirect.py