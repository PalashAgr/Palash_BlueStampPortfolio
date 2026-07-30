# Ball Tracking Rover
The project involves building a Raspberry PI-based robot that tracks a ball as a simulation of sample and hazard detection. It uses the OpenCV python library for computer vision, which is used to draw bounding boxes around where the ball could possibly be. In addition, the rover performs topography analysis on factors such as tilt and orientation to determine its location, while also tracking planets.
<!--- This is an HTML comment in Markdown -->
<!--- Anything between these symbols will not render on the published site -->

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Palash A | Cupertino HS | Aerospace Engineering | Incoming Junior

![Headshot](headshot.jpg)
  
<!--**# Final Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.yout ube.com/embed/F7M7imOVGug" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your final milestone, explain the outcome of your project. Key details to include are:
- What you've accomplished since your previous milestone
- What your biggest challenges and triumphs were at BSE
- A summary of key topics you learned about
- What you hope to learn in the future after everything you've learned at BSE-->

# Third Milestone
## Summary
  For my 3rd milestone, I wrote the full code for the rover to track the ball, move, and avoid obstacles. I wrote all my code in the Thonny python editor, which was built in to the raspberry pi computer. To track the ball, I defined 2 color ranges to create a binary mask, where pixels whose color is in the range(s) are shown as a white pixel in the mask, while the rest of the pixels are shown as black. The program draws an ellipse around the largest contour, or outline of a shape, and assumes that is the ball. From the ellipse, it extracts we can extract the x and y coordinates of the ball's center. After this, the ultrasonic sensors send out pulses to get the nearest obstacle distance, and depending on how small those distances are, the rover will either back up, turn right, or change the outputs of the motor pins to move forward, backward, left, or right, towards the ball. If the ball is not in frame, the rover will keep rotating counterclockwise until it finds the ball.
  
## Challenges
  One of the challenges with the camera was changing when the frames are converted from RGB to BGR or HSV, which are two other types of color ranges. I had to experiment with the placements of these conversions to make sure that the camera was seeing accurately, specifically it should not see red objects as blue and vice versa. Additionally, I had to spend a lot of time tweaking the color ranges for the mask so that it does not pick up other objects in similar color. There were also some logic issues in the code I had to fix so that the rover actually avoids obstacles. Part of the problem was that the camera could not keep up with the rover's movement, so I had to edit my searching algorithm such that it turns and stops regularly (rotating in intervals).

## Next Steps
  Now that the main project is completed, I will start working on my modifications. The first modification is topography analysis, using an IMU to analyze and graph values for pitch, roll, and temperature over time. The IMU I have uses the MPU6050 library, and I would use python's matplotlib library to make the graph. My other modification is to use onshape to model a cover for the rover, to make it look unique.

# Second Milestone
## Summary
  For my 2nd milestone, I wired the raspberry pi, motor driver h-bridge, and ultrasonic sensors to the base of the rover. Using the schematic I made on fritzing, I started by connecting the switches on the motor driver to the motors on the sides of the robot, as well as the battery wires. Each of the sensors had 4 wires: Ground, power, echo, and trig. The ground, power, and echo wires connected to the breadboard, while the trig wires connected to the raspberry pi. For each of these sensors, I also installed a voltage divider on the breadboard. This was necessary to bring the 5V voltage in the sensors down to 3.3V so that it is compatible with the raspberry pi. After this, I tested the motors, camera module, and ultrasonic sensors using testing code to test functionality. In the process of conducting these tests, I enabled SSH on my raspberry PI so that I can remotely access the PI monitor through my own laptop using RealVNC Connect Viewer.
## Challenges
  One of the challenges I had when physically doing the wiring was creating the voltage dividers. I had to conduct some research and learn a bit more about how voltage dividers work, and I went through many stages of wiring before achieving the correct setup. Later on, another challenge I encountered was setting up SSH. Sometimes, the monitor took a long time to turn on, and there was a very long process Raspberry Pi imager had to undergo to install SSH. However, now it is easier to log into the monitor quickly and write code. Specific to the testing code, sometimes there were issues with python syntax and unimported libraries, but now I was able to verify that the picamera worked, the ultrasonic sensors had accurate measurements, and I can also control robot movement using WASD, just like in a video game.
## Next Steps
  The hardware is now completely setup and mounted, so now I plan to start writing full code for the robot. I will be using the Thonny python editor on the raspberry pi software, which I also used for the testing code. Currently, my logic is to use the openCV library to create a mask to track where the ball is continuously in each frame, and have the robot turn or move forward accordingly.


<!--<iframe width="560" height="315" src="https://www.youtube.com/embed/y3VAmNlER5Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your second milestone, explain what you've worked on since your previous milestone. You can highlight:
- Technical details of what you've accomplished and how they contribute to the final goal
- What has been surprising about the project so far
- Previous challenges you faced that you overcame
- What needs to be completed before your final milestone -->
<!--**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/CaCazFBhYKs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your first milestone, describe what your project is and how you plan to build it. You can include:
- An explanation about the different components of your project and how they will all integrate together
- Technical progress you've made so far
- Challenges you're facing and solving in your future milestones
- What your plan is to complete your project -->
# First Milestone
## Summary
  My project is a ball tracking rover that uses raspberry PI to perform topography analysis, planet tracking, and also create a graph       charting the ball's distance from the robot. After creating diagrams on paper and a schematic online, for my first milestone I have completed the base of th robot, which included attaching the motors, the battery case, and wheels. 
## Challenges
  While assembling the hardware, sometimes it was hard to tell which size screws were needed to mount a component. Initially, my screws to secure the battery case were too small and kept falling out, however I eventually pivoted to a larger size which worked better in securing it. Additionally, when making the schematic online on fritzing, the hardest part was making the voltage divider on the breadboard. Before making the schematic, I did not have a ton of electrical experience, but eventually I was able to learn how they work. In the schematic below, you can see that there are 3 voltage dividers, 1 for each sensor, and the resistors are in parallel.
  ![schematic](schematic.jpg)
  note: Left sensor trig wire has been moved to pin 15 (GPIO 22), left sensor echo wire connected to breadboard moved to pin 13 (GPIO 27).
  
## Next Steps
  Now that the base of the robot is assembled and planning has been done, I will need to wire the electronics together on the robot using the schematic. Once all these electronics are funcitoning correctly and are mounted onto the robot, I can start writing the full code for the robot.
<!--Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resoruces to create professional schematic diagrams, though BSE recommends Tinkercad becuase it can be done easily and for free in the browser. -->

# Starter Project
## Summary
  For my starter project I chose the retro arcade console. The console has 5 games in its system (which I didn't correctly figure out until after filming the milestone video). Much of the project encompassed soldering buttons and other game components onto a PCB. After screwing on the battery case on the back, I screwed on the front and back lids of the console. Overall, this starter project helped me solidify my soldering skills.
## Challenges
  A lot of times when I was soldering I accidentally added too much solder, which was especially tedious to avoid for smaller solder points that were closer together. If two solder points are connected by solder, it will cause a short circuit. Fortunately, I learned a couple of techniques to fix these errors. A lot of times, applying the soldering iron on the solder will remelt it and make it flow into the hole. I also ended up using the solder sucker a lot to remove excess solder from the board.

<!---# Code
Here's where you'll put your code. The syntax below places it into a block of code. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize it to your project needs. 

```c++
void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  Serial.println("Hello World!");
}

void loop() {
  // put your main code here, to run repeatedly:

Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 
} -->

# Bill of Materials

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Raspberry Pi 4 | Contains the microcomputer where code is uploaded to, and controls what actions other parts perform | $38.50 | <a href="https://www.adafruit.com/product/4295?gad_source=1&gad_campaignid=21079227318&gbraid=0AAAAADx9JvSGLBIm3AzeKDsMgLScOARTP&gclid=CjwKCAjwmJjSBhB-EiwAkZgxi-BMiWTt63thvUL53uiCCwRKV9zTqj1L6AnmZTy36jFEQFqJ9GdmBRoCNYUQAvD_BwE"> Link </a> |
| Raspberry Pi Camera Module | Camera that enables the robot to see and track the ball | $17.50 | <a href="https://vilros.com/products/products-raspberry-pi-camera-module-v2?variant=41308152627294&country=US&currency=USD&utm_medium=product_sync&utm_source=google&utm_content=sag_organic&utm_campaign=sag_organic&tw_source=google&tw_adid=&tw_campaign=19684058556&gad_source=1&gad_campaignid=19684058613&gbraid=0AAAAAD1QJAgA2hfDQwtcLNVkXxnWLVsF3&gclid=CjwKCAjwpK3SBhASEiwAtV1SPIN0OsGS5exVahvvqlmi4ZyuIY9AEKJi6pscUGfG7IIYwvgnaQwhyRoChTcQAvD_BwE"> Link </a> |
| L298N Driver Board | Provides power to the motors, in different combinations that affect the movement of the robot, which is determined by the code uploaded into the raspberry pi | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Motors and Board Kit | Contains all the parts needed to assemble the base of the robot | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Power bank | Makes the rover be able to travel portably by powering the raspberry pi (instead of connecting a wire to a port limiting its range) | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
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
