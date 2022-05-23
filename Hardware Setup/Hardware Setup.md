# Hardware Setup

Build chassis by following [these instructions](https://www.tamiya.com/english/rc/rcmanual/tt02.pdf)

Add additional hardware following [these instructions](https://github.com/NVIDIA-AI-IOT/jetracer/blob/master/docs/tamiya/hardware_setup.md) and using [these materials](https://docs.google.com/spreadsheets/d/1pdqG1og2lO-83MmD-lcoXxOteeDbbvSXhTYG8bqrR_c/edit#gid=0)

<a></a>
<img src="https://user-images.githubusercontent.com/63427135/168500687-ad4661b6-5f82-4241-8919-696a458ca27a.PNG" height=256/>
<img src="https://user-images.githubusercontent.com/63427135/168500690-5759eff2-9824-472d-88e4-285a429eb189.PNG" height=256/>
<img src="https://user-images.githubusercontent.com/63427135/168500692-c557416f-b7f9-44a6-8bca-3c4c24fd9156.PNG" height=256/>

Follow below wiring configurations for manual and software control. The manual control configuration should work for both manual and software control if the MUX is calibrated correctly. Because of troubles with calibrating the MUX, a software only configurartion will work, too.

<a></a>
<img src="https://user-images.githubusercontent.com/63427135/168498556-cdc4d5ee-a995-49c8-9392-bad7b588ca0c.PNG" height=350/>
<img src="https://user-images.githubusercontent.com/63427135/168498559-c709fb0e-91d3-4d10-84bf-55ff26cfcc3a.PNG" height=350/>

Test that hardware is setup correctly by following the [basic motion](https://github.com/NVIDIA-AI-IOT/jetracer/blob/master/notebooks/basic_motion.ipynb) example

# Basic Motion Notes

- car.steering and car.throttle will accept any value within range [-1.0, 1.0]
- From calibration testing, we found that the car has a complete steering range of [-0.5, 0.5] with 0.1 resolution when 0 points the wheels forward
- The throttle must receive a value of at least 0.15 to begin moving
- The JetRacer will stop when throttle is set to 0, reach max speed when set to 1, reach minimum speed when set to 0.125, and can reverse when set to a negative value after being stopped. The JetRacer will stop moving if you set throttle to a negative value when it is moving forward.

# Example User Guide

```python
from jetracer.nvidia_racecar import NvidiaRacecar

car = NvidiaRacecar()

car.steering_offset = 0.1  # calibrate for each car

car.throttle = 0.0   # stops car
car.steering = 0.0   # wheels point forward

def steer_forward():
car.steering = 0.0

# setting steering to negative makes JetRacer turn right
def steer_max_right():
car.steering = -1.0

# setting steering to positive makes JetRacer turn left
def steer_max_left():
car.steering = 1.0

def steer_slight_right():
  if (car.steering >= -0.9):
 car.steering = car.steering - 0.1

def steer_slight_left():
  if (car.steering <= 0.9):
 car.steering = car.steering + 0.1

def throttle_max():
car.throttle = 1.0

def throttle_min():
car.throttle = 0.15
car.throttle = 0.125

def throttle_mid():
car.throttle = 0.15

def throttle_accelerate():
if (car.throttle + 0.25 <= 1.0):
car.throttle = car.throttle + 0.025

def throttle_decelerate():
if (car.throttle - 0.25 >= 0):
car.throttle = car.throttle - 0.025

def throttle_stop():
car.throttle = 0.0

# setting throttle to negative when stopped should make the JetRacer reverse
def throttle_reverse():
car.throttle = 0.0
car.throttle = -0.15
```

# Future Work

1. Calibrate the MUX so that user input from the remote control can overwrite software control from the Jetson Nano. The JetRacer is designed so that manual input will always take priority when the transmitter is on, but the team could not get the JetRacer to accept manual and software input simultaneously to control the car.
2. Move the JetRacer in reverse, and calibrate the speed of moving in reverse. Although JetRacer documents claim that the JetRacer will reverse when throttle is set to a negative value when the car is stopped, the team could not get the JetRacer to reverse. More troubleshooting or adding hardware like an H-bridge is necessary to solve this problem.


```python

```
