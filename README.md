# Eleksmaker Elekslaser A3
This is to document my settings and additions for my Elekslaser A3.
It was later modified with an additional Z-Axis and a spindle.

They are currently more my personal notes, but might be useful to others too.

## Firmware

Get the latest `grbl` version at https://github.com/gnea/grbl/releases
The boards are shipped with grbl 0.9. Upgrading to 1.1 brings several improvements.

### Updating 

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

## grbl configuration

My grbl config is stored in the [grbl-config](grbl-config) folder.
The ones with a ´-default´ suffix are the one as shipped. They are just stored for reference.

### Notes

Make sure to enable laser mode. But also disable it when using the spindle.

#### Z-Axis
The steps per mm is different than for the other steppers. ´400´ worked well for me

I also had to set several bitmasks to invert directions. But that might be related to how i positioned the end-switches.

## components

I started with a basic EleksLaser A3, but soon decided i wanted to add a Z-Axis and endswitches.

The links are just examples, and not necessarily exactly what I ordered.

- Important! [proper laser safety googles](https://www.amazon.de/gp/product/B07Z9742H5/ref=ppx_yo_dt_b_asin_title_o06_s00?ie=UTF8&psc=1) - at least OD4+ is needed.
- [2 Axis Laser](https://www.banggood.com/EleksMaker-EleksLaser-A3-Pro-2500mW-Laser-Engraving-Machine-CNC-Laser-Printer-p-1003863.html?rmmds=search&cur_warehouse=CN)
- [3 Axis Control Board](https://www.banggood.com/EleksMaker-Mana-3-Axis-Stepper-Motor-Driver-Board-Controller-For-DIY-Laser-Engraver-p-1015947.html?rmmds=detail-top-buytogether-auto&cur_warehouse=USA)
- [Z-Axis & Spindle](https://www.banggood.com/EleksMaker-EleksZAxis-Z-Axis-Spindle-Motor-Drill-Chunk-Integrated-Set-DIY-Upgrade-Kit-for-Laser-Engraver-CNC-Router-p-1435867.html?rmmds=detail-top-buytogether-auto&cur_warehouse=CN)

- [External Control Board for Endswitches](https://www.banggood.com/EleksMaker-EleksExtra-External-Control-Board-Add-XYZ-Limit-Probe-Coolant-Spindle-Functions-OnOff-Button-For-Mana-ManaSE-Stepper-Motor-Driver-Board-p-1481516.html?rmmds=search&cur_warehouse=CN)
In my case this unexpectedly included the endwitches even.

- [JST plugs](https://www.amazon.de/gp/product/B01MY8FLMV/ref=ppx_yo_dt_b_asin_image_o04_s00?ie=UTF8&psc=1)

- several cables to extend the original ones, as they are sometimes short

## Software

### Laser
- [Laser grbl](http://lasergrbl.com/) is a great software for almost everything laser related. I can really recommend.

### CNC / Drawing

- AutoDesk [Fusion 360](https://www.autodesk.de/products/fusion-360/overview) - its free for personal use. I had to customize the post processor for the laser part to make it work. My custom version is [here](fusion360/post)

### running / milling

- [cncjs](https://cnc.js.org/) - i use cncjs on a raspberry to actually run the generated gcode and to operate the machine
- [ser2net](https://linux.die.net/man/8/ser2net) - running on the raspberry. to directly connect from Laser GRBL to the machine over wifi.


## links
Other documents from others that helped me a lot

- [https://github.com/jandelgado/eleksmaker_a3](https://github.com/jandelgado/eleksmaker_a3)
- modding [https://itink.it/wiki/doku.php?id=en:tinkering:laser:eleksmakera3pro#grbl_settings](https://itink.it/wiki/doku.php?id=en:tinkering:laser:eleksmakera3pro#grbl_settings)