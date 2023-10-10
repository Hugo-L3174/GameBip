# GameBip

Since this project uses [Lakka](http://www.lakka.tv/) it is able to run on a lightweight Raspberry pi zero2.
The drivers can be adapted and compiled from source for another hardware platform.

## Screen driver
The driver is [fbcp-ili9341](https://github.com/juj/fbcp-ili9341) (see details).

At runtime the driver looks by default for the symbolic link libbcm_host.so.0 to the libbcm_host.so library object. It is not always present by default on the lakka releases so we create it in our custom lib folder and export its path for runtime:
```shell
ln -s /usr/lib/libbcm_host.so /storage/testDrivers/libbcm_host.so.0
```
and then exporting it before starting the driver in /storage/.config/autostart.sh:
```shell
export LD_LIBRARY_PATH=/storage/testDrivers:$LD_LIBRARY_PATH
```

## Buttons driver
Lakka does not allow remapping using python scripts so we will use Adafruit's [Retrogame](https://github.com/adafruit/Adafruit-Retrogame)

## config.txt
we use the legacy vc4-fkms-v3d driver instead of vc4-kms-v3d and use the following hdmi parameters to make the best use of [fbcp-ili9341](https://github.com/juj/fbcp-ili9341) on the 2.2" tft

```shell
dtoverlay=vc4-fkms-v3d

hdmi_force_hotplug=1
hdmi_timings=320 0 8 32 40 240 1 3 4 6 0 0 0 40 0 4048000 1
hdmi_group=2
hdmi_mode=87

```

## .config/autostart.sh
```shell
export LD_LIBRARY_PATH=/storage/testDrivers:$LD_LIBRARY_PATH
/storage/testDrivers/fbcp-ili9341 &
/storage/testDrivers/retrogame /storage/testDrivers/retrogame.cfg &
```