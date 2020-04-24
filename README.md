# Eleksmaker Elekslaser A3
This is to document my settings and additions for my Elekslaser A3

## Firmware
Get the latest `grbl` version at https://github.com/gnea/grbl/releases

Install `avrdude`

```bash
sudo apt install avrdude
```

Backup the firmware

```bash
sudo avrdude -c arduino -b 57600 -P /dev/ttyUSB0 -p atmega328p -vv -U flash:r:grbl_v0.9-eleksmana5.2.hex
```

Flash the new firmware

```bash
sudo avrdude -c arduino -b 57600 -P /dev/ttyUSB0 -p atmega328p -vv -U flash:w:grbl_v1.1h.20190825.hex
```
