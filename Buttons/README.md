We simply use the compiled driver from [Retrogame](https://github.com/adafruit/Adafruit-Retrogame) that remaps GPIO entries as virtual keyboard entries.

Autostarting the script and giving it our config as argument is done by adding this in /storage/.config/autostart.sh
```shell
/storage/testDrivers/retrogame /storage/testDrivers/retrogame.cfg &
```

The Retrogame driver is mapped to the following pins (see retrogame.cfg):
```shell
LEFT      18  # Joypad left
RIGHT     24  # Joypad right
DOWN       5  # Joypad down
UP         6  # Joypad up
Z         12  # 'A' button
X         13  # 'B' button
A         16  # 'X' button
S         19  # 'Y' button
Q         20  # Left shoulder button
W         21  # Right shoulder button
ESC       17  # Exit ROM; PiTFT Button 1
LEFTCTRL  22  # 'Select' button; PiTFT Button 2
ENTER     23  # 'Start' button; PiTFT Button 3
4         27  # PiTFT Button 4
```
As they are left free by the PITFT 2.2" we use (ref: ADA 2315).