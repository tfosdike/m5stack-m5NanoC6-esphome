# m5stack-m5NanoC6-esphome

Includes all hardware available on NanoC6: IR-transmitter, LED, RGB+RGB-power, button and support for m5stack ENV.IV sensor board.

I've added a windows docker config for a sample home assistant server.

## Installing the firmware

(Windows)

 - Set up SSID and passwords in a secrets.yaml file
 - Install Python+esphome as per https://esphome.io/guides/installing_esphome.html#windows
 - USB connect your m5NanoC6
 - In a terminal, go to this folder and build the image using `esphome run .\m5stack_nano-c6.yaml`.  This can take a while the first time, as it needs to download compilers and libraries
 - Select USB update
 
### IP address

If you don't want to set up a DHCP reservation, you can set an IP address in the configuration YAML.  

```
#######################################################
wifi:
  ssid:        !secret wifi_ssid
  password:    !secret wifi_password
  manual_ip:
    static_ip: <ip_address>
####################################################### 
```

## Run server

You'll need a linux server or docker.  I'm assuming this is running docker on Windows

Run `docker compose up -d` in the docker_cfg folder.

Open a browser to http://localhost:8123 (and set up the password if you need to)

Assuming mDNS isn't set up, you'll neet to add the device manually:

Settings->Add Integration->ESPHome->enter IP address

