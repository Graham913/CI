# CI
# CircuitPython
 The follwing files are my first foray into CircuitPython.
## Table of Contents
* [Table of Contents](#TableOfContents)
* [Hello_CircuitPython](#Hello_CircuitPython)
* [CircuitPython_Servo](#CircuitPython_Servo)
* [CircuitPython_LCD](#CircuitPython_LCD)
* [NextAssignmentGoesHere](#NextAssignment)
---

## Hello_CircuitPython

### Description & Code
Description goes here

Here's how you make code look like code:

```python
Code goes here
import board
import neopixel
import time
dot = neopixel.NeoPixel(board.NEOPIXEL, 1)


while True:
    print("Make it green!")
    dot.fill((0,255,0))
    time.sleep(.5)
    print("Make it red!")
    dot.fill((255,0,0))
    time.sleep(.5)
    print("Make it blue!")
    dot.fill((0,174,255))
    time.sleep(.5)
```


### Evidence
![graham pic1](https://i.ytimg.com/vi/X_TXoVbq9oo/maxresdefault.jpg)
### Images
I just used the neopixel that was built into the adafruit metro express
### Reflection
it was relatively easy but I forgot how to make the neopixel blink from last time we used it so after I watched the video it made sense.




## CircuitPython_Servo

### Description & Code

```python

import time
import board
import pwmio
import servo
import touchio
# create a PWMOut object on Pin A2.
pwm = pwmio.PWMOut(board.A2, duty_cycle=2 ** 15, frequency=50)
touch_pad1 = board.A1  # Will not work for Circuit Playground Express!
touch1 = touchio.TouchIn(touch_pad1)
touch_pad2 = board.A3  # Will not work for Circuit Playground Express!
touch2 = touchio.TouchIn(touch_pad2)

# Create a servo object, my_servo.
my_servo = servo.Servo(pwm)

while True:
    if touch1.value:
        print("Touched A1!")
        for angle in range(0, 180, 1):  # 0 - 180 degrees, 5 degrees at a time.
            my_servo.angle = angle
            time.sleep(0.01)
    if touch2.value:
        print("Touched A3!")
        for angle in range(180, 0, -1):   # 180 - 0 degrees, 5 degrees at a time.
            my_servo.angle = angle
            time.sleep(0.01)
    time.sleep(0.05)

```

### Evidence

### Images

### Reflection




## CircuitPython_LCD

### Description & Code

```python
Code goes here

```

### Evidence

### Images

### Reflection





## NextAssignment

### Description & Code

```python
Code goes here

```

### Evidence

### Images

### Reflection
