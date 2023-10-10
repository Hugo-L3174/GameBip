The driver [fbcp-ili9341](https://github.com/juj/fbcp-ili9341) is compiled using the following options 
```shell
$ -DSPI_BUS_CLOCK_DIVISOR=6 -DADAFRUIT_ILI9341_PITFT=ON -DBACKLIGHT_CONTROL=ON
```
(Note: this is missing the option to get rid of the statistics so as is they are overlayed on the screen.)

THERE IS NO CROSS COMPILATION 
The driver has to be compiled on the hardware it will run on so the compiled driver here is for the raspberry pi zero 2.