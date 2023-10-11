The driver [fbcp-ili9341](https://github.com/juj/fbcp-ili9341) is compiled using the following options 
```shell
$ -DSPI_BUS_CLOCK_DIVISOR=6 -DADAFRUIT_ILI9341_PITFT=ON -DBACKLIGHT_CONTROL=ON
```
(Note: this is missing the -DSTATISTICS=0 option to get rid of the statistics so as is they are overlayed on the screen.)

WARNING: By default the hardware is autodetected! Unless the specific options for the target hardware and instruction set are passed, the driver is compiled for the hardware that runs the make command. 
The precompiled driver here is for the raspberry pi zero 2.