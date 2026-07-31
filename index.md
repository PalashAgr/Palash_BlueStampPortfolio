# Ball Tracking Rover
The project involves building a Raspberry PI-based rover that tracks a ball as a simulation of sample and hazard detection. It uses the OpenCV python library for computer vision, which is used to draw bounding boxes around where the ball could possibly be. In addition, the rover performs topography analysis on factors such as tilt and temperature and graphs data for pitch, roll, and temperature.
<!--- This is an HTML comment in Markdown -->
<!--- Anything between these symbols will not render on the published site -->

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Palash A | Cupertino HS | Aerospace Engineering | Incoming Junior

![Headshot](headshot.jpg)
  
# Final Milestone

## Summary
  For my final milestone, I implemented both of my modifications. The first one was to perform topography analysis, using data from an IMU. The IMU measures angular acceleration in the x, y, and z directions. I used these values to calculate pitch, roll, and temperature, the latter of which is also directly measured by the IMU. Then, I used python's Matplot lib library to graph the 3 quantities. To make this process simpler, I put all my IMU code in a separate file before integrating it into the main.py file. My other modification involved modeling a cover for the rover using CAD. I ended up making it 9 parts total, and when the parts arrived I had to remove a bunch of supports and paint all the components before attaching it to the rover to achieve the final product.

## Challenges
  Before I could start wiring my IMU, my picamera module broke off, possibly by dropping the rover by accident, so I had to place it back while also correcting the cover in OxnShape so that the hole for the camera mount is aligned with the camera itself. Later, when I was testing my IMU code, my sensor library was unable to be used, and I thought I had to setup a virtual environment, which I also thought broke my main code somehow. However, it turns out the process of reattaching the camera mount was the source of the error, and I ended up spending an entire session replacing cameras and ribbon cables numerous times, until it magically worked the next session. Going back to the library issue, I tried deactivating the virtual environment and using a different terminal command to install the library, and somehow it worked. In summary, these were two completely different issues that I thought were related in some way, and while this confusion took a lot of time to resolve, it was by far the most effective at teaching me the importance of persevearance at Bluestamp.

## Next Steps
  Now that my project at Bluestamp is finished, I can say that I have learned a lot of skills in electrical and software engineering. This program was most effective at teaching me how to use a variety of electrical components like a raspberry pi, motor driver, an IMU, and some ultrasonic sensors. As for software, I learned how to be resourceful and use the internet to find articles, blogs, and other resources to help me with implementing code for my project. I also got a lot more comfortable using terminal. Overall, the skills that I have learned at Bluestamp will help me do a lot more in my extracurricular activities at school. In the future, I hope to continue to practice my software skills for these types of projects and also learn how to design printed circuit boards (or PCBs).

# Third Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/7O53WqhYHmw?si=ZB7aB7B37jeF74bX" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Summary
  For my 3rd milestone, I wrote the full code for the rover to track the ball, move, and avoid obstacles. I wrote all my code in the Thonny python editor, which was built in to the raspberry pi computer. To track the ball, I defined 2 color ranges to create a binary mask, where pixels whose color is in the range(s) are shown as a white pixel in the mask, while the rest of the pixels are shown as black. The program draws an ellipse around the largest contour, or outline of a shape, and assumes that is the ball. From the ellipse, it extracts we can extract the x and y coordinates of the ball's center. After this, the ultrasonic sensors send out pulses to get the nearest obstacle distance, and depending on how small those distances are, the rover will either back up, turn right, or change the outputs of the motor pins to move forward, backward, left, or right, towards the ball. If the ball is not in frame, the rover will keep rotating counterclockwise until it finds the ball.
  
## Challenges
  One of the challenges with the camera was changing when the frames are converted from RGB to BGR or HSV, which are two other types of color ranges. I had to experiment with the placements of these conversions to make sure that the camera was seeing accurately, specifically it should not see red objects as blue and vice versa. Additionally, I had to spend a lot of time tweaking the color ranges for the mask so that it does not pick up other objects in similar color. There were also some logic issues in the code I had to fix so that the rover actually avoids obstacles. Part of the problem was that the camera could not keep up with the rover's movement, so I had to edit my searching algorithm such that it turns and stops regularly (rotating in intervals).

## Next Steps
  Now that the main project is completed, I will start working on my modifications. The first modification is topography analysis, using an IMU to analyze and graph values for pitch, roll, and temperature over time. The IMU I have uses the MPU6050 library, and I would use python's matplotlib library to make the graph. My other modification is to use onshape to model a cover for the rover, to make it look unique.

# Second Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/idbZXTeBtoM?si=icZICjPYDa-tGBc9" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Summary
  For my 2nd milestone, I wired the raspberry pi, motor driver h-bridge, and ultrasonic sensors to the base of the rover. Using the schematic I made on fritzing, I started by connecting the switches on the motor driver to the motors on the sides of the rover, as well as the battery wires. Each of the sensors had 4 wires: Ground, power, echo, and trig. The ground, power, and echo wires connected to the breadboard, while the trig wires connected to the raspberry pi. For each of these sensors, I also installed a voltage divider on the breadboard. This was necessary to bring the 5V voltage in the sensors down to 3.3V so that it is compatible with the raspberry pi. After this, I tested the motors, camera module, and ultrasonic sensors using testing code to test functionality. In the process of conducting these tests, I enabled SSH on my raspberry PI so that I can remotely access the PI monitor through my own laptop using RealVNC Connect Viewer.
## Challenges
  One of the challenges I had when physically doing the wiring was creating the voltage dividers. I had to conduct some research and learn a bit more about how voltage dividers work, and I went through many stages of wiring before achieving the correct setup. Later on, another challenge I encountered was setting up SSH. Sometimes, the monitor took a long time to turn on, and there was a very long process Raspberry Pi imager had to undergo to install SSH. However, now it is easier to log into the monitor quickly and write code. Specific to the testing code, sometimes there were issues with python syntax and unimported libraries, but now I was able to verify that the picamera worked, the ultrasonic sensors had accurate measurements, and I can also control rover movement using WASD, just like in a video game.
## Next Steps
  The hardware is now completely setup and mounted, so now I plan to start writing full code for the rover. I will be using the Thonny python editor on the raspberry pi software, which I also used for the testing code. Currently, my logic is to use the openCV library to create a mask to track where the ball is continuously in each frame, and have the rover turn or move forward accordingly.

# First Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/f4T_GTdz6V4?si=UMWHPVf3lki_EbNt" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Summary
  My project is a ball tracking rover that uses raspberry PI to perform topography analysis, planet tracking, and also create a graph       charting the ball's distance from the rover. After creating diagrams on paper and a schematic online, for my first milestone I have completed the base of th rover, which included attaching the motors, the battery case, and wheels. 
## Challenges
  While assembling the hardware, sometimes it was hard to tell which size screws were needed to mount a component. Initially, my screws to secure the battery case were too small and kept falling out, however I eventually pivoted to a larger size which worked better in securing it. Additionally, when making the schematic online on fritzing, the hardest part was making the voltage divider on the breadboard. Before making the schematic, I did not have a ton of electrical experience, but eventually I was able to learn how they work. In the schematic below, you can see that there are 3 voltage dividers, 1 for each sensor, and the resistors are in parallel.
  ![schematic](schematic.jpg)
  note: Left sensor trig wire has been moved to pin 15 (GPIO 22), left sensor echo wire connected to breadboard moved to pin 13 (GPIO 27).
  
## Next Steps
  Now that the base of the rover is assembled and planning has been done, I will need to wire the electronics together on the rover using the schematic. Once all these electronics are funcitoning correctly and are mounted onto the rover, I can start writing the full code for the rover.
<!--Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resoruces to create professional schematic diagrams, though BSE recommends Tinkercad becuase it can be done easily and for free in the browser. -->

# Starter Project

<iframe width="560" height="315" src="https://www.youtube.com/embed/h5othK2I87I?si=C7HyL0KQWkRsdQdP" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Summary
  For my starter project I chose the retro arcade console. The console has 5 games in its system (which I didn't correctly figure out until after filming the milestone video). Much of the project encompassed soldering buttons and other game components onto a PCB. After screwing on the battery case on the back, I screwed on the front and back lids of the console. Overall, this starter project helped me solidify my soldering skills.
## Challenges
  A lot of times when I was soldering I accidentally added too much solder, which was especially tedious to avoid for smaller solder points that were closer together. If two solder points are connected by solder, it will cause a short circuit. Fortunately, I learned a couple of techniques to fix these errors. A lot of times, applying the soldering iron on the solder will remelt it and make it flow into the hole. I also ended up using the solder sucker a lot to remove excess solder from the board.

# Code
## Camera Testing Code
```python
import cv2
from picamera2 import Picamera2
import RPi.GPIO as GPIO
import time              
import numpy as np

picam2 = Picamera2()
picam2.configure(picam2.create_preview_configuration())
picam2.start()

while True:
    frame = picam2.capture_array()

    cv2.imshow("Camera", frame)

    if cv2.waitKey(1) == ord('q'):
        break

picam2.stop()
cv2.destroyAllWindows()
```
## Motor Testing Code
```python
import RPi.GPIO as GPIO
import cv2
import numpy as np
        
GPIO.setmode(GPIO.BCM)
        
MOTORAB=9 # RIGHT motor
MOTORAA=25
        
MOTORBA=15 # LEFT motor
MOTORBB=23 
        
GPIO.setup(MOTORAA, GPIO.OUT)
GPIO.setup(MOTORAB, GPIO.OUT)
        
GPIO.setup(MOTORBA, GPIO.OUT)
GPIO.setup(MOTORBB, GPIO.OUT)

motor_pwm1 = GPIO.PWM(MOTORAA, 1000)
motor_pwm1.start(0)  # Initial duty cycle is 0 (stopped)
speed = 60
motor_pwm2 = GPIO.PWM(MOTORAB, 1000)
motor_pwm2.start(0)  # Initial duty cycle is 0 (stopped)
motor_pwm3 = GPIO.PWM(MOTORBA, 1000)
motor_pwm3.start(0)  # Initial duty cycle is 0 (stopped)
motor_pwm4 = GPIO.PWM(MOTORBB, 1000)
motor_pwm4.start(0)  # Initial duty cycle is 0 (stopped)

while(True):
    userInput = input()  
    if(userInput == 'd'):
        GPIO.output(MOTORAA,GPIO.HIGH)
        motor_pwm1.ChangeDutyCycle(speed)
        GPIO.output(MOTORAB,GPIO.LOW)
        motor_pwm2.ChangeDutyCycle(0)
        GPIO.output(MOTORBA,GPIO.HIGH)
        motor_pwm3.ChangeDutyCycle(speed)
        GPIO.output(MOTORBB,GPIO.LOW)
        motor_pwm4.ChangeDutyCycle(0)
        print("d pressed")
            
    if(userInput == 's'):
        print("s pressed")
        GPIO.output(MOTORAA,GPIO.LOW)
        motor_pwm1.ChangeDutyCycle(0)
        GPIO.output(MOTORAB,GPIO.HIGH)
        motor_pwm2.ChangeDutyCycle(speed)
        GPIO.output(MOTORBA,GPIO.HIGH)
        motor_pwm3.ChangeDutyCycle(speed)
        GPIO.output(MOTORBB,GPIO.LOW)
        motor_pwm4.ChangeDutyCycle(0)
                
    if(userInput == 'a'):
        print("a pressed")
        GPIO.output(MOTORAA,GPIO.LOW)
        motor_pwm1.ChangeDutyCycle(0)
        GPIO.output(MOTORAB,GPIO.HIGH)
        motor_pwm2.ChangeDutyCycle(speed)
        GPIO.output(MOTORBA,GPIO.LOW)
        motor_pwm3.ChangeDutyCycle(0)
        GPIO.output(MOTORBB,GPIO.HIGH)
        motor_pwm4.ChangeDutyCycle(speed)
            
    if(userInput == 'w'):
        print("w pressed")
        GPIO.output(MOTORAA,GPIO.HIGH)
        motor_pwm1.ChangeDutyCycle(speed)
        GPIO.output(MOTORAB,GPIO.LOW)
        motor_pwm2.ChangeDutyCycle(0)
        GPIO.output(MOTORBA,GPIO.LOW)
        motor_pwm3.ChangeDutyCycle(0)
        GPIO.output(MOTORBB,GPIO.HIGH)
        motor_pwm4.ChangeDutyCycle(speed)
        
    if(userInput == 'x'):
        print("x pressed")
        GPIO.output(MOTORAA,GPIO.LOW)
        motor_pwm1.ChangeDutyCycle(0)
        GPIO.output(MOTORAB,GPIO.LOW)
        motor_pwm2.ChangeDutyCycle(0)
        GPIO.output(MOTORBA,GPIO.LOW)
        motor_pwm3.ChangeDutyCycle(0)
        GPIO.output(MOTORBB,GPIO.LOW)
        motor_pwm4.ChangeDutyCycle(0)
```
## Sensor Testing Code
```python
import RPi.GPIO as GPIO
import time
GPIO.setmode(GPIO.BCM)
        
TRIG_PIN = 3#left: 20. Middle: 4. Right: 3.
ECHO_PIN =  2#left: 26. Middle: 17. Right: 2.
        
GPIO.setup(TRIG_PIN, GPIO.OUT)
GPIO.setup(ECHO_PIN, GPIO.IN)
GPIO.output(TRIG_PIN, GPIO.LOW)
        
time.sleep(0.1)
        
GPIO.output(TRIG_PIN, GPIO.HIGH)
        
time.sleep(0.1)
        
GPIO.output(TRIG_PIN, GPIO.LOW)
TIMEOUT = 0.02

pulse_send = time.time()
start_timeout = time.time()
while GPIO.input(ECHO_PIN) ==0:
    pulse_send=time.time()
    print("pulse_send " + str(pulse_send))
    if (pulse_send - start_timeout) > TIMEOUT:
        print("Timeout waiting for echo start")
        break
pulse_received = time.time()
end_timeout = time.time()
while GPIO.input(ECHO_PIN) ==1:
    pulse_received=time.time()
    print("pulse received " + str(pulse_received))
    if (pulse_received - end_timeout) > TIMEOUT:
        print("Timeout waiting for echo end")
        break
if (pulse_send - start_timeout) < TIMEOUT and (pulse_received - end_timeout) < TIMEOUT:            
    pulse_duration=pulse_received - pulse_send
    pulse_duration=pulse_duration/2
    print("pulse duration " + str(pulse_duration))
        
    distance = 34300 * pulse_duration #speed of sound (cm/s) = 34300
    distance = round(distance,2)
    print("distance is " + str(distance))
```
## IMU testing Code
```python
import RPi.GPIO as GPIO
import time              
import numpy as np
import smbus
import math
from mpu6050 import mpu6050
import matplotlib.pyplot as plt
sensor = mpu6050(0x68)
bus = smbus.SMBus(1)
p = np.array([])
r = np.array([])
t = np.array([])
n = 0
while n < 10:
    accel = sensor.get_accel_data()
    #Pitch = atan2(a_y, sqrt(a_z^2 + a_x^2)
    pitch = math.atan2(accel['z'], math.sqrt(accel['x']**2 + accel['y']**2))
    roll = math.atan2(accel['y'], math.sqrt(accel['x']**2 + accel['z']**2))
    p = np.append(p, pitch)
    r = np.append(r, roll)
    #Roll = atan2(a_x, sqrt(a_z^2 + a_y^2)
    temp = sensor.get_temp()
    t = np.append(t, temp)
    print("Pitch " + str(pitch) + " Roll " + str(roll) + " Temperature " + str(temp))
    print(" ")
    time.sleep(0.1)
    n = n + 1
print(p)
print(r)
print(t)

fig, ax = plt.subplots(3)
ax[0].plot(r, color='blue', marker='o', linestyle='--'); ax[0].set_title("Roll")
ax[0].set_ylim(-1, 1)
ax[1].plot(p, color='green', marker='o', linestyle='--'); ax[1].set_title("Pitch")
ax[1].set_ylim(-2, 2)
ax[2].plot(t, color='red', marker='o', linestyle='--'); ax[2].set_title("Temperature")
ax[2].set_ylim(0, 40)

# Display the window
plt.show()
    

```
## Full code for Rover
```python
import cv2
from picamera2 import Picamera2
import RPi.GPIO as GPIO
import time              
import numpy as np
from gpiozero import DistanceSensor
from gpiozero.pins.pigpio import PiGPIOFactory
import smbus
import math
from mpu6050 import mpu6050
import matplotlib.pyplot as plt

GPIO.setmode(GPIO.BCM)
factory = PiGPIOFactory()

#define GPIO pins
BA = 15 # pin 10
BB = 23 # pin 16
AA = 25 # pin 22
AB = 9 # pin 21
TRIGL = 20 # pin 38
TRIGM = 4 # pin 7
TRIGR = 22 # pin 15
ECHOL = 26 # pin 37
ECHOM = 17 # pin 11
ECHOR = 27 # pin 13

#Define sensors
leftSensor = DistanceSensor(echo=ECHOL, trigger=TRIGL, pin_factory=factory)
midSensor = DistanceSensor(echo=ECHOM, trigger=TRIGM, pin_factory=factory)
rightSensor = DistanceSensor(echo=ECHOR, trigger=TRIGR, pin_factory=factory)

#Relevant 
CAM_X = 160
CAM_Y = 120
i = True
detected = False
alternator = True
controller = True
speed = 90
area = 0

#Setup motor mins
GPIO.setup(AA, GPIO.OUT)
GPIO.setup(AB, GPIO.OUT)     
GPIO.setup(BA, GPIO.OUT)
GPIO.setup(BB, GPIO.OUT)

#left sensor
GPIO.setup(TRIGL, GPIO.OUT)
GPIO.setup(ECHOL, GPIO.IN)
GPIO.output(TRIGL, GPIO.LOW)        
time.sleep(0.1)        
GPIO.output(TRIGL, GPIO.HIGH)        
time.sleep(0.1)
GPIO.output(TRIGL, GPIO.LOW)

#middle sensor
GPIO.setup(TRIGM, GPIO.OUT)
GPIO.setup(ECHOM, GPIO.IN)
GPIO.output(TRIGM, GPIO.LOW)        
time.sleep(0.1)        
GPIO.output(TRIGM, GPIO.HIGH)        
time.sleep(0.1)
GPIO.output(TRIGM, GPIO.LOW)

#Right sensor
GPIO.setup(TRIGR, GPIO.OUT)
GPIO.setup(ECHOR, GPIO.IN)
GPIO.output(TRIGR, GPIO.LOW)        
time.sleep(0.1)        
GPIO.output(TRIGR, GPIO.HIGH)        
time.sleep(0.1)
GPIO.output(TRIGR, GPIO.LOW)

#Setup pwm for motors (speed control)
motor_pwm1 = GPIO.PWM(AA, 1000)
motor_pwm1.start(0)  # Initial duty cycle is 0 (stopped)
motor_pwm2 = GPIO.PWM(AB, 1000)
motor_pwm2.start(0)  # Initial duty cycle is 0 (stopped)
motor_pwm3 = GPIO.PWM(BA, 1000)
motor_pwm3.start(0)  # Initial duty cycle is 0 (stopped)
motor_pwm4 = GPIO.PWM(BB, 1000)
motor_pwm4.start(0)  # Initial duty cycle is 0 (stopped)
    
def turnLeft(rate):
    GPIO.output(AA,GPIO.LOW)
    motor_pwm1.ChangeDutyCycle(0)
    GPIO.output(AB,GPIO.HIGH)
    motor_pwm2.ChangeDutyCycle(speed * rate)
    GPIO.output(BA,GPIO.LOW)
    motor_pwm3.ChangeDutyCycle(0)
    GPIO.output(BB,GPIO.HIGH)
    motor_pwm4.ChangeDutyCycle(speed * rate)
    print("left")
    
def turnRight(rate):
    GPIO.output(AA,GPIO.HIGH)
    motor_pwm1.ChangeDutyCycle(speed * rate)
    GPIO.output(AB,GPIO.LOW)
    motor_pwm2.ChangeDutyCycle(0)
    GPIO.output(BA,GPIO.HIGH)
    motor_pwm3.ChangeDutyCycle(speed * rate)
    GPIO.output(BB,GPIO.LOW)
    motor_pwm4.ChangeDutyCycle(0)
    print("right")
def moveForward(rate):
    GPIO.output(AA,GPIO.HIGH)
    motor_pwm1.ChangeDutyCycle(speed * rate)
    GPIO.output(AB,GPIO.LOW)
    motor_pwm2.ChangeDutyCycle(0)
    GPIO.output(BA,GPIO.LOW)
    motor_pwm3.ChangeDutyCycle(0)
    GPIO.output(BB,GPIO.HIGH)
    motor_pwm4.ChangeDutyCycle(speed * rate)
    print("forward")
def moveBackward(rate):
    GPIO.output(AA,GPIO.LOW)
    motor_pwm1.ChangeDutyCycle(0)
    GPIO.output(AB,GPIO.HIGH)
    motor_pwm2.ChangeDutyCycle(speed * rate)
    GPIO.output(BA,GPIO.HIGH)
    motor_pwm3.ChangeDutyCycle(speed * rate)
    GPIO.output(BB,GPIO.LOW)
    motor_pwm4.ChangeDutyCycle(0)
    print("backward")
def stop():
    GPIO.output(AA,GPIO.LOW)
    motor_pwm1.ChangeDutyCycle(0)
    GPIO.output(AB,GPIO.LOW)
    motor_pwm2.ChangeDutyCycle(0)
    GPIO.output(BA,GPIO.LOW)
    motor_pwm3.ChangeDutyCycle(0)
    GPIO.output(BB,GPIO.LOW)
    motor_pwm4.ChangeDutyCycle(0)
    print("stop")
    
#Compute distance from nearest obstacle using sensor data, constants, and formulas
def distance(ECHO_PIN):
    TIMEOUT = 0.02
    pulse_send = time.time()
    start_timeout = time.time()
    while GPIO.input(ECHO_PIN) ==0:
        pulse_send=time.time()
        if (pulse_send - start_timeout) > TIMEOUT:
            break
    pulse_received = time.time()
    end_timeout = time.time()
    while GPIO.input(ECHO_PIN) ==1:
        pulse_received=time.time()
        if (pulse_received - end_timeout) > TIMEOUT:
            break
    if (pulse_send - start_timeout) < TIMEOUT and (pulse_received - end_timeout) < TIMEOUT:            
        pulse_duration=pulse_received - pulse_send
        pulse_duration=pulse_duration/2
        distance = 34300 * pulse_duration #speed of sound (cm/s) = 34300
        distance = round(distance,2)
        return distance
    else:
        return -1
    
#IMU setup
try:
    sensor = mpu6050(0x68)
    bus = smbus.SMBus(1)
except:
    print("Error")
p = np.array([]) #pitch data
r = np.array([]) #roll data
t = np.array([]) # temp data
time_axis = np.array([])

#Color Ranges
COLOR_LOWER = np.array([0, 180, 135]) 
COLOR_UPPER = np.array([7, 255, 255])
CL1 = np.array([168, 180, 135])
CL2 = np.array([180, 255, 255])

# Initialize webcam (0 is usually the default built-in camera)
# Initialize Picamera2picam = Picamera2()
picam = Picamera2()
picam.configure(picam.create_preview_configuration(main={"size": (320, 240)}))
picam.start()
time.sleep(2)
moveForward(0.6)
time.sleep(0.1)
stop()
start = time.monotonic_ns() // 1_000_000
last = start
while True:
    detected = False
    #capture a frame
    frame = picam.capture_array() 
    resize = cv2.resize(frame, (320, 240))
    blur = cv2.GaussianBlur(resize, (5, 5), 0)
    
    #Convert RGB image to HSV for the mask
    image = cv2.cvtColor(blur, cv2.COLOR_RGB2HSV)
    
    # Create a binary mask where the ball's color shows up as white
    mask = cv2.inRange(image, COLOR_LOWER, COLOR_UPPER) + cv2.inRange(image, CL1, CL2)
    kernel = np.ones((5, 5), np.uint8)
    erode = cv2.erode(mask, kernel, iterations=1)
    dilate = cv2.dilate(erode, kernel, iterations=1)
    
    # Find outlines and show mask
    edged = cv2.Canny(dilate, 30, 200)
    contours, hierarchy = cv2.findContours(edged, cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_NONE)
    cv2.imshow("Mask", mask)
    
    #Convert RGB image to BGR for picam display
    frame = cv2.cvtColor(resize, cv2.COLOR_RGB2BGR)
    
    xpos = None
    ypos = None
    if len(contours) >= 1:
        # Find the largest contour, assuming it is our ball
        ball = max(contours, key=cv2.contourArea)
        
        #Try to draw an ellipse around ball if it is big enough
        axes = (0, 0)
        if ball is not None and len(ball) >= 5 and cv2.contourArea(ball) > 10: 
            ellipse = cv2.fitEllipse(ball)
            xpos = int(ellipse[0][0])
            ypos = int(ellipse[0][1])
            center = (xpos, ypos)
            axes = (int(ellipse[1][0] / 2), int(ellipse[1][1] / 2))
            a = int(axes[0] / 2)
            b = int(axes[1] / 2)
            
            area = np.pi * a * b
        # Check if ellipse is closeg enough to look like a circle
        aspect_ratio = float(axes[0]) / axes[1] if axes[1] != 0 else 0
        if 0.6 < aspect_ratio < 1.4:
            
            # Draw the reconstructed full circle/ellipse from the arc
            cv2.ellipse(frame, ellipse, (0, 255, 0), 2)
            cv2.circle(frame, center, 3, (0, 0, 255), -1)

    #Display camera
    cv2.imshow("Ball Tracking Rover", frame)
            

    if i == True:
        #Get sensor distances
        distanceL = leftSensor.distance * 100
        distanceM = midSensor.distance * 100
        distanceR = rightSensor.distance * 100
        
        #Max distance to back up
        THRESH_LOWER = 8
        # max distance to have to turn away
        THRESH_UPPER = 17
    
        # back up if too close
        if int(distanceL) <= THRESH_LOWER or int(distanceM) <= THRESH_LOWER or int(distanceR) <= THRESH_LOWER:
            moveBackward(0.8)
            print("******* OBSTACLE VERY CLOSE *************")
            detected = True
            
        # turn away if obstacle is close unless ball area is very big, whcih means the ball is found
        elif area >= 2000 or int(distanceL) <= THRESH_UPPER or int(distanceM) <= THRESH_UPPER or int(distanceR) <= THRESH_UPPER:
            if area >= 2000:
                print('BALL FOUND!')
                stop()
                break
            if controller == True:
                turnRight(1)
                controller = False
            else:
                stop()
                controller = True
            print("********* OBSTACLE DETECTED ***********")
            detected = True
        else:
            detected = False
    
    if i == False or detected == False:
        
        # rotate turning left if ball not found
        if xpos == None or ypos == None:
            if alternator == True:
                turnLeft(1)
                alternator = False
            else:
                stop()
                alternator = True
            print("Searching...")
        else:
            #distance from camera center to ball
            dx = CAM_X - xpos
            dy = CAM_Y - ypos
            
            #if ball is on the left then turn left
            if dx > 100:
                turnLeft(0.6)
                
            #if ball is on the right then turn right
            elif dx < -100:
                turnRight(0.6)
            
            #move forward if ball is in the middle zone
            elif dy >= -100 and dy <=100:
                moveForward(1)
            
            #fail safe if none of the conditions above run
            else:
                stop()
                print("BALL IS NEAR")
                
    #Wait for 200 milliseconds to get data from IMU            
    while True:
        #print("hi")
        now = time.monotonic_ns() // 1_000_000
        dt = now - last
        #print("startSearch is " + str(startSearch) + ", currentSearch is " + str(currentSearch) + ", search is " + str(search))
        if dt >= 200:
            time_data = (now - start) / 1000
            #Add time coordinate values
            time_axis = np.append(time_axis, time_data)
            last = now
            break
        
    try:
        #Get accel data and use formulas to get pitch and roll
        accel = sensor.get_accel_data()
        
        #Pitch = atan2(a_y, sqrt(a_z^2 + a_x^2)
        pitch = math.atan2(accel['z'], math.sqrt(accel['x']**2 + accel['y']**2))
        
        #Roll = atan2(a_x, sqrt(a_z^2 + a_y^2)
        roll = math.atan2(accel['y'], math.sqrt(accel['x']**2 + accel['z']**2))
        
        #Add data to arrays
        p = np.append(p, pitch)
        r = np.append(r, roll)
        
        #Get temperature data and add to data array
        temp = sensor.get_temp()
        t = np.append(t, temp)
    except:
        print("reading failed")
        
    #Stop camera if q is pressed
    if cv2.waitKey(1) & 0xFF == ord('q'):
        stop()
        print("q pressed")
        break
    
picam.stop()
picam.close()

#Graph the 3 quantities (pitch, roll, temp) as subplots
fig, ax = plt.subplots(3)
ax[0].plot(time_axis, r, color='blue', marker='.', linestyle='--'); ax[0].set_title("Roll")
ax[0].set_ylim(-1.5, 1.5)
ax[1].plot(time_axis, p, color='green', marker='.', linestyle='--'); ax[1].set_title("Pitch")
ax[1].set_ylim(-2, 2)
ax[2].plot(time_axis, t, color='red', marker='.', linestyle='--'); ax[2].set_title("Temperature")
ax[2].set_ylim(0, 40)
plt.tight_layout()
cv2.destroyAllWindows()
plt.show()
```

# Bill of Materials

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Raspberry Pi 4 | Contains the microcomputer where code is uploaded to, and controls what actions other parts perform | $38.50 | <a href="https://www.adafruit.com/product/4295?gad_source=1&gad_campaignid=21079227318&gbraid=0AAAAADx9JvSGLBIm3AzeKDsMgLScOARTP&gclid=CjwKCAjwmJjSBhB-EiwAkZgxi-BMiWTt63thvUL53uiCCwRKV9zTqj1L6AnmZTy36jFEQFqJ9GdmBRoCNYUQAvD_BwE"> Link </a> |
| Raspberry Pi Camera Module | Camera that enables the rover to see and track the ball | $17.50 | <a href="https://vilros.com/products/products-raspberry-pi-camera-module-v2?variant=41308152627294&country=US&currency=USD&utm_medium=product_sync&utm_source=google&utm_content=sag_organic&utm_campaign=sag_organic&tw_source=google&tw_adid=&tw_campaign=19684058556&gad_source=1&gad_campaignid=19684058613&gbraid=0AAAAAD1QJAgA2hfDQwtcLNVkXxnWLVsF3&gclid=CjwKCAjwpK3SBhASEiwAtV1SPIN0OsGS5exVahvvqlmi4ZyuIY9AEKJi6pscUGfG7IIYwvgnaQwhyRoChTcQAvD_BwE"> Link </a> |
| L9110 Driver Board | Provides power to the motors, in different combinations that affect the movement of the rover, which is determined by the code uploaded into the raspberry pi | $33.66 | <a href="https://www.amazon.com/L9110S-Stepper-Driver-Temperature-Arduino/dp/B0FP5R55GB"> Link </a> |
| Motors and Board Kit | Contains all the parts needed to assemble the base of the rover | $19.99 | <a href="https://www.rovershop.com/products/xiaor-geek-2wd-rover-car-chassis-kit-with-tt-motor-battery-box-acrylic-chassis-and-2-wheels-diy-project-smart-rover-chassis-rovers-car-platform-arduino-raspberry-pi?gad_source=1&gad_campaignid=20145188159&gbraid=0AAAAAD_f_xywtUFradOcL9MJx_2a-CICa&gclid=CjwKCAjwj7HTBhBiEiwA8s35OgwA-PxTNSUEWVRB7kyCOXV9RV8SHChpfO1VwdJjvLmFbZ22sCJGtxoCrRMQAvD_BwE"> Link </a> |
| Power bank | Makes the rover be able to travel portably by powering the raspberry pi (instead of connecting a wire to a port limiting its range) | $29.99 | <a href="https://www.bestbuy.com/product/anker-power-bank-10k-22-5w-built-in-usb-c-cable-black/JJ858RLKLP/sku/6643854?utm_source=feed&extStoreId=1423&ref=212&loc=19561581008&gclsrc=aw.ds&gad_source=4&gad_campaignid=19562380540&gbraid=0AAAAAD-ORIiSjEtY-C0k9kfqrJplTjRcn&gclid=CjwKCAjwj7HTBhBiEiwA8s35OjykyXxQzE5dt1055VoaGhJWS23tOMHjG--XQwz13TsbSrepLcI0LBoCxd8QAvD_BwE"> Link </a> |
| HC-SR04 Sensors (5 pcs) | Sends and receives a signal and measures the time in between the pulses. This time can be used to calculate the distance to the nearest obstacle. | $5.25 | <a href="https://www.sparkfun.com/ultrasonic-distance-sensor-hc-sr04.html?srsltid=AfmBOoqFrVAtpwHDCejRn62wEtzgnn7pZzJ7Wjbl_NNX58lybzk9adbq"> Link </a> |
| HDMI to micro HDMI cable | Allows the raspberry pi to connect to a monitor with keyboard and mouse, or just a laptop after SSH has been setup | $6.99 | <a href="https://www.amazon.com/UGREEN-Adapter-Ethernet-Compatible-Raspberry/dp/B06WWQ7KLV?th=1"> Link </a> |
| Video Capture Card | Used to display picamera using OBS, which can be projected without Wifi | $15.99 | <a href="https://www.amazon.com/Capture-1080P60-Streaming-Recorder-Compatible/dp/B08Z3XDYQ7?th=1"> Link </a> |
| SD Card Reader | Enables picamera to be shown remotely | $5.99 | <a href="https://www.walmart.com/ip/USB-3-0-SD-Micro-SD-card-reader-SD-TF-memory-external-suitable-SD-SDXC-SDHC-MMC-RS-MMC-Micro-SDHC-Card-etc/7123373632?wmlspartner=wlpa&selectedSellerId=102726243&adid=222222222277123373632_102726243_14069003552_202077872&wl0=&wl1=g&wl2=c&wl3=42423897272&wl4=pla-2449037643288&wl5=9032183&wl6=&wl7=&wl8=&wl9=pla&wl10=5557717621&wl11=online&wl12=7123373632_102726243&veh=sem&gad_source=1&gad_campaignid=202077872&gbraid=0AAAAADmfBIr8qx1C41iHfkiXub36i37Vs&gclid=CjwKCAjwpqHTBhAcEiwAj2AfunXKcwSFwjiy-G4T5ILvrSDk6ew_c1LDinfBMRplty9cQcDtJ6YATBoCbEsQAvD_BwE"> Link </a> |
| Basic Connections Components Kit | Contains jumper wires which are primarily used to create the voltage dividers on the breadboard | $10.60 | <a href="https://www.digikey.com/en/products/detail/bud-industries/BC-32626/5291560?gclsrc=aw.ds&gad_source=1&gad_campaignid=20232005509&gbraid=0AAAAADrbLlhYGjx1hri3mwVbTplsA0TMC&gclid=CjwKCAjwsfzSBhB5EiwAOGyqSaWfFZ-PQZIniYwwyta05ZzSblONG60Tda5WEF7z-3xyNA6KWB3CqxoCTZwQAvD_BwE"> Link </a> |
| Female to Female Jumper Wires| One of the types of wires used to connect the components | $1.95 | <a href="https://www.digikey.com/en/products/detail/adafruit-industries-llc/1950/6827084?gclsrc=aw.ds&gad_source=1&gad_campaignid=20232005509&gbraid=0AAAAADrbLljptrgFyBRhANVYO4nOwL4mw&gclid=CjwKCAjwx7LSBhB3EiwAjcodxMaqXD3yC4neFOcPBvp2WLxwl1qzc0lilNy_xKyJw9D0pvGeaAex9BoC6K0QAvD_BwE&__cf_chl_f_tk=Uia7vvSdgHEdaC.xTbj.fXW9Tw4Fg0STdL_glbliS3g-1783438661-1.0.1.1-jvd.UjjxgvLWgold6_GjzJ8gw_qMrPcZQiDYgfDZ4KU"> Link </a> |
| Soldering Kit | Used to solder lose wire ends and permanantely attach breadboard wiring to perf board (breadboard is only temporary) | $51.99 | <a href="https://www.amazon.com/gp/aw/d/B09TXP1KDV/?_encoding=UTF8&pd_rd_plhdr=t&aaxitk=84d81372b709bb6a1b2aa42a5f3e1a9a&hsa_cr_id=0&qid=1784648426&sr=1-1-9e67e56a-6f64-441f-a281-df67fc737124&i=aps&aref=sKRejGvEwE&ref_=sbx__sbtcd_asin_0_title&pd_rd_w=gVsLw&content-id=amzn1.sym.2fb72bc8-96ef-420d-b08f-c04b69f36507%3Aamzn1.sym.2fb72bc8-96ef-420d-b08f-c04b69f36507&pf_rd_p=2fb72bc8-96ef-420d-b08f-c04b69f36507&pf_rd_r=BAN7CRC0FSH8P87DS95Q&pd_rd_wg=LP2R5&pd_rd_r=65142355-ccda-48fe-83fe-0a0c353bb247"> Link </a> |

# Other Resources/Examples
<!--One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.-->
- [gpiozero library documentation](https://gpiozero.readthedocs.io/en/stable/api_input.html)
- [Geeksforgeeks](https://www.geeksforgeeks.org/python/circle-detection-using-opencv-python/)
- [makersportal](https://makersportal.com/blog/calibration-of-an-inertial-measurement-unit-with-raspberry-pi?srsltid=AfmBOooq1QSGR5yEc7tFMCLZ8EB6_s41uGYW7iHP91mnt7EcI4H8SxMY)
- [Blog on implementing an IMU](https://sharad-rawat.medium.com/interface-an-inertial-measurement-unit-imu-with-raspberry-pi-3d7b9583db09)
- [Geeksforgeeks matplot article](https://www.geeksforgeeks.org/python/plot-multiple-plots-in-matplotlib/)
