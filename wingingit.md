# Just wing it

Resources:

- https://learn.adafruit.com/adafruit-hallowing
- Add 
https://adafruit.github.io/arduino-board-index/package_adafruit_index.json

to the board manager URL:

sudo cp 99-adafruit-boards.rules /etc/udev/rules.d/
sudo reload udev
sudo usermod -a -G dialout $USER
sudo usermod -a -G plugdev $USER 

^ Use the correct install script for that

```CPP
// the setup function runs once when you press reset or power the board
void setup() {
  // initialize digital pin 13 as an output.
  pinMode(13, OUTPUT);
}
 
// the loop function runs over and over again forever
void loop() {
  digitalWrite(13, HIGH);   // turn the LED on (HIGH is the voltage level)
  delay(1000);              // wait for a second
  digitalWrite(13, LOW);    // turn the LED off by making the voltage LOW
  delay(1000);              // wait for a second
    digitalWrite(13, HIGH);    // turn the LED off by making the voltage LOW
  delay(1000);              // wait for a second
    digitalWrite(13, LOW);    // turn the LED off by making the voltage LOW
  delay(1000);              // wait for a second
}
```


# Circuit Python

https://circuitpython.org/board/hallowing_m0_express/

wget https://github.com/adafruit/circuitpython/releases/download/4.0.1/adafruit-circuitpython-hallowing_m0_express-en_US-4.0.1.uf2

https://learn.adafruit.com/adafruit-hallowing/circuitpython

https://codewith.mu/

```python
import board
import digitalio
import time
 
led = digitalio.DigitalInOut(board.D13)
led.direction = digitalio.Direction.OUTPUT
 
while True:
    led.value = True
    time.sleep(0.5)
    led.value = False
    time.sleep(0.5)

```

TODO: Set a vim swapfile directory haha.

Otherwise: `vim -n` or `:noswapfile`

## Serial

`tail -f /dev/ttyACM0`

Test it:

```python

import board
import digitalio
import time
 
led = digitalio.DigitalInOut(board.D13)
led.direction = digitalio.Direction.OUTPUT
 
while True:
    print("Hello, CircuitPython!")
    led.value = True
    time.sleep(1)
    led.value = False
    time.sleep(1)
```

Libs: https://github.com/adafruit/Adafruit_CircuitPython_Bundle/releases/download/20190528/adafruit-circuitpython-bundle-4.x-mpy-20190528.zip

Old info, but useful general stuff. (*.mpy isn't a thing any more I believe): https://learn.adafruit.com/circuitpython-essentials/circuitpython-expectations#how-can-i-create-my-own-mpy-files-18-6

Be sure to copy libs into a `lib/` folder
