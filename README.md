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
Make the neopixel built into the adafruit metro express change colors and say what color it is in the serial monitor 
I used the dot.fill code to make the neopixel change colors and I used the time.sleep command to make it sleep in between colors and I used the print command to say what color it is on the serial monitor.

Here's how you make code look like code:

```python
Code goes here
import board
import neopixel
import time
dot = neopixel.NeoPixel(board.NEOPIXEL, 1)


while True:
    print("Make it green!") # makes serial monitor say Make it green!
    dot.fill((0,255,0))  # rgb color code for green
    time.sleep(.5) # sleep inbetween switching colors
    print("Make it red!")
    dot.fill((255,0,0))
    time.sleep(.5)
    print("Make it blue!")
    dot.fill((0,174,255))
    time.sleep(.5)
```


### Evidence
![graham pic1](https://i.ytimg.com/vi/X_TXoVbq9oo/maxresdefault.jpg)
Adafruit metro express with white neopixel turned on
### Images
I just used the neopixel that was built into the adafruit metro express
### Reflection
it was relatively easy but I forgot how to make the neopixel blink from last time we used it so after I watched the video it made sense.




## CircuitPython_Servo

### Description & Code
Make a servo move using capacitive touch
I used two wires to make a servo move either left or right using capacitive touch
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
        for angle in range(0, 180, 1):  # 0 - 180 degrees, 5 degrees at a time. # moves servo one direction 180 degrees when I touch a wire
            my_servo.angle = angle
            time.sleep(0.01)
    if touch2.value:
        print("Touched A3!")
        for angle in range(180, 0, -1):   # 180 - 0 degrees, 5 degrees at a time. # moves servo another direction 180 degrees when I touch a wire
            my_servo.angle = angle
            time.sleep(0.01)
    time.sleep(0.05)

```

### Evidence
![Captouch wiring](https://user-images.githubusercontent.com/71406930/133624920-48544cc9-975f-4714-98aa-9c8a3528aef3.png)
wiring for capacitive touch, the two wires sticking out are what I used for the capacitive touch
### Images
![ezgif com-gif-maker](https://user-images.githubusercontent.com/71406930/133623520-758b1186-d83c-476a-808e-5f681fed7ae7.gif)

### Reflection
You can get a lot of information in the adafruit forums and that helped a lot in this assignment. Finding the order of the indents to optimize speed for the wires to register touch is key so thats why I have my whole code so I don't forget how to.



## CircuitPython_distance sensor
Make the neopixel change from red to blue to green graduaolly using the distance sensor

I used the MAP function to gradually change the colors of the neopixel when I moved my phone further away from it
### Description & Code

```python
Code goes here
import time
import board
import adafruit_hcsr04
import neopixel
import simpleio

sonar = adafruit_hcsr04.HCSR04(trigger_pin=board.D5, echo_pin=board.D6) # pins for ultrasonic sensor
dot = neopixel.NeoPixel(board.NEOPIXEL, 1)
dot.brightness = 0.5

cm = 0
print("new code!")

while True:
    try:
        cm = sonar.distance
        print((cm,))

        if cm < 5: # if the distance is less than 5 cm the color is red
            dot.fill((255, 0, 0))
        elif cm < 20: # if distance is above 5 cm gradually change to blue until 20 cm
            r = simpleio.map_range(cm, 5, 20, 255, 0)
            g = 0
            b = simpleio.map_range(cm, 5, 20, 0, 255)
            dot.fill((int(r), int(g), int(b)))
        else: # if distance is above 20 cm gradually change to green
            r = 0
            g = simpleio.map_range(cm, 20, 35, 0, 255)
            b = simpleio.map_range(cm, 20, 35, 255, 0)
            dot.fill((int(r), int(g), int(b)))
    except RuntimeError:
        print("Retrying!")
    time.sleep(0.1)

```

### Evidence
![ezgif com-gif-maker (1)](https://user-images.githubusercontent.com/71406930/134513956-0c523336-479d-4557-9cab-a61886148155.gif)
### Images
![distance.sensor](https://user-images.githubusercontent.com/71406930/134190731-f80e0f4c-b342-412d-a34d-da1487bf9d50.png)
ultrasonic sensor to detect how far something is away and shown with neopixel
### Reflection
Using the simpleio library and memorizing the html color codes can help with this as well as an understanding of variables. Using old code can reducing work time and speeds everything up so if you have old code make sure to use it.




## NextAssignment

### Description & Code

```python
Code goes here

```

### Evidence

### Images

### Reflection
