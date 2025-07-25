&nbsp;

🛠️ Engineering Documentation 🛠️
======

> This repository details Team Asparagus’ building and programming process in our second participating year of the 2024 WRO Future Engineers Competition.
&nbsp; 

---

## Content of Repository 
* `models` - 3D CAD files
* `others` - Other essential files
* `schemes` - Electrical schematics
* `src` - Main and other programs to run/control software
* `t-photos` - Team photos
* `v-photos` - Robot photos
* `video` - Video demonstration
&nbsp; 

Team Members
---

* Kayla Lin, 17, kylln2027@gmail.com
* Eric Rao, 16, ericrao08@gmail.com
* Brian Yin, 17, brianyin256@gmail.com

<img src="https://github.com/kylln20/WRO_FE_2023-24/blob/main/t-photos/Team_Official.jpg" width="40%" height="40%"> <img src="https://github.com/kylln20/WRO_FE_2023-24/blob/main/t-photos/Team_Funny.jpg" width="40%" height="40%">

***Kayla Lin (Left), Eric Rao (Middle), Brian Yin (Right)***

## 📖 Content of README 📖
* **[Hardware](#-hardware-)**
  * [Components](#%EF%B8%8F-components-%EF%B8%8F)
  * [Mobility Management](#-mobility-management-)
    * [Chassis](#chassis)
    * [Design](#design)
    * [Motors](#motors)
  * [Power and Sense Management](#-power-and-sense-management-)
    * [Power and Wiring](#power-and-wiring)
    * [Sensors](#sensors)
    * [Schematic](#schematic)
* **[Software](#-software-)**
  * [Initialization and Connection Process](#-initialization-and-connection-process-)
  * [Object Management](#object-management)
    *  [Object Detection](#object-detection--open-challenge--obstacle-challenge-)
    *  [Wall Detection/Management](#wall-detectionmanagement--open-challenge--obstacle-challenge-)
    *  [Signal Pillar Detection/Management](#signal-pillar-detectionmanagement--obstacle-challenge-)
    *  [Turning (Open Challenge)](#turning--open-challenge-)
    *  [Turning (Obstacle Challenge)](#turning--obstacle-challenge-)
    *  [Parking Lot Detection/Management](#parking-lot-detectionmanagement--obstacle-challenge-)
    *  [Three-Point Turn](#three-point-turn--obstacle-challenge-)
    *  [Backing Up](#backing-up--obstacle-challenge-)
    *  [Potential Improvement: Stuck Detection](#potential-improvement-stuck-detection--open-challenge--obstacle-challenge-)
* **[Assembly Instructions](#-complete-assembly-instructions-)**
  
&nbsp;

---

&nbsp;

🤖 Hardware 🤖
===


### ⚙️ Components ⚙️

| Name | Product | Price |
| ----------- | ----------- | ----------- |
| RC Car | [`Carisma GT24`](https://www.canadahobbies.ca/product/hobby-brands/carisma-rc/gt24-124th-4wd-toyota-celica-gt-four-st185-wrc/) | $263 |
| RC Car Battery | [`Gens Ace 1300mAh Battery`](https://www.adrenalinehobby.com/products/gens-ace-g-tech-1300mah-2s-7-4v-25c-lipo-deans-plug) | $35 | 
| Drive Motor & ESC | [`Furitek Komodo Motor + Lizard Pro ESC`](https://www.xtremerc.ca/products/furitek-scx24-stinger-brushless-power-system-w-1212-3450kv-brushless-motor?_pos=1&amp;_sid=cf7c35a05&amp;_ss=r) | $226 |
| Turning Motor | [`Hitec HS-5055MG Servo Motor`](https://ca.robotshop.com/products/hs-5055mg-metal-gear-micro-servo-motor?srsltid=AfmBOopv8Z7LoCVOEqe16w05ZV-R78dNmy7dappldIxZiQzCJroxcssFc2Y) | $38 |
| Motor Mount | [`GT24 High Performance Alloy Motor Mount`](https://carisma-shop.com/products/gt24-alum-motor-mount) | $17 |
| CSI Camera | [`SainSmart Wide Angle Fish-Eye Camera`](https://www.amazon.ca/SainSmart-Fish-Eye-Camera-Raspberry-Arduino/dp/B00N1YJKFS/ref=sr_1_5) | $19 |
| Raspberry Pi HAT | [`HiWonder TurboPi HAT`](https://www.hiwonder.com/collections/raspberrypi-bionic-robot/products/turbopi?variant=40112905388119) | $61 [^1] |
| Raspberry Pi | [`Vemico Raspberry Pi 4`](https://www.amazon.ca/Vemico-Raspberry-Kit-Heatsinks-Screwdriver/dp/B09WXRCYL4/ref=sr_1_3) | $176 |
| Raspberry Pi Fan | [`GeeekPi Fan`](https://www.amazon.ca/dp/B07C9H9LJN?psc=1&ref=ppx_yo2ov_dt_b_product_details) | $19 |
| ON OFF Switch | [`DaierTek Switch`](https://a.co/d/05vnrpJD) | $13 |

**Total Car Cost: $867 CAD**

[^1]: This link is for the `Hiwonder TurboPi Car`, which uses the `HiWonder TurboPi HAT`. We contacted the manufacturer to purchase the HAT directly.

<sup>*3D printed parts were made with the [`BambuLab P1P`](https://ca.store.bambulab.com/products/p1p)</sup>

&nbsp;

🚗 Mobility Management 🚗
---

### Chassis
We use the chassis of the `Carisma GT24`, a pre-built 1/24 scale RC car (15 cm in length) to accommodate the added challenge of the magenta parking lot in the obstacle challenge. It allows us to park head-on, as opposed to parallel parking. Head-in parking has fewer steps, reducing our obstacle challenge time. Also, while head-in parking, the car only needs to be aware of what is beside it and what is in front of it, which can be assessed with a single front-facing camera. Comparatively, to perform parallel parking, a car will usually need to reverse, requiring an additional rear-facing sensor. Such would unnecessarily complicate the system.

The chassis also enables a four-wheel drive system, with pre-integrated gearboxes. This system offers benefits over a two-wheel drive system increasing the car's traction, stability, and acceleration due to the power distribution between four wheels instead of two. 

#### Potential Chassis Improvement
Although the chassis has many benefits, its design only allows a maximum turning angle of 50 degrees. Although sufficient for our task, a car with a chassis with a greater turning angle would more easily navigate the challenges and could be pushed to navigate at a higher speed. Swapping the chassis for one with a higher turning angle, whether store-bought or 3D-printed, would significantly improve the car's movement and obstacle avoidance. We have also seen that one can modify the original chassis to have a much greater turning angle, but we decided against it due to time constraints. 

This is a video example of a modification done to a similar chassis: 

[K989 Modification](https://www.youtube.com/watch?v=JmsCxSgEJnU)

### Design 

<img src="https://github.com/kylln20/WRO_FE_2023-24/blob/main/other/extra%20images/Labeled3.jpg" height="300px"> <img src="https://github.com/kylln20/WRO_FE_2023-24/blob/main/other/extra%20images/Labeled4.jpg" height="300px">

1. **Base Nut Front / Back**: used to secure the 3D-printed base onto the chassis
2. **Cable Barrier**: is attached to the chassis to prevent cables from interfering with tires
4. **Camera Mount**: the piece the camera is attached to, adds height and tilt
6. **Car Base**: the main platform of the car, is attached to the chassis through 4 posts, components of the base include:
    - Holder for Raspberry Pi
    - Holder for cooling fan 
    - Holder for battery
    - Vertical post to route battery cable
    - Cable ladder organizer on the right side
    - Hook on the left to hold the power cable in place
7. **Servo Attachment**: attaches to the servo motor and controls steering

The design of the camera mount changed from our national competition with it becoming one singular piece mounted directly on the printed car base. 

It used to be three seperate pieces, mounted to thin plastic posts on the chassis. 

This redesign allowed for a much more sturdy camera mount ensuring the camera is stable during object detection. 

### Motors
Our car uses a `Furitek Micro Komodo Brushless Motor`. Brushless motors refer to the lack of small "brushes" in the motor that a brushed motor would have. This design reduces motor friction, improving lifespan, torque, efficiency, and acceleration. Adequate torque is essential during slow turns to avoid cogging.

The `Furitek Micro Komodo Brushless Motor` is also very small compared to other RC car motors, making it fit well with our small chassis. It fits conveniently in the place of the original motor, with a metal gearhead that connects to the rest of the drive system. Despite its size, the motor is remarkably powerful. With a KV (RPM/Motor) of 3450, this motor allows us to reach high speeds without maxing out the motor. 

The Motor is mounted on an aluminum motor mount for increased durability and passive cooling. 

The motor receives power and signal via PWM from the `Furitek Lizard Pro Electronic Speed Controller (ESC)`. This ESC provides constant regulation that ensures we can maintain a constant pace, with smooth acceleration and deceleration.

To control steering we use a `Hitec HS-5055MG Servo Motor`, a three-wire connection (signal, voltage, ground) metal gear servo motor. We control and power it from the `Raspberry Pi Hardware Attached on Top (HAT)`. The original 5-wire servo that came with the RC chassis had a weaker plastic gear and was non-programmable due to being connected to a customized circuit board. Due to both those flaws, we replaced the original servo. 

The servo is connected to the front wheel axis with a 3D-printed adapter piece that is screwed onto the servo shaft. It has a torque of about 1.5kg/cm at 6V allowing it to quickly and precisely change the direction of our car. This precision is vital for our needs in the obstacle challenge and open challenge.

&nbsp;

⚡ Power and Sense Management ⚡
---

### Power and Wiring
Our car gets power from a single `Gens Ace 1300mAh 7.4V Battery`. This battery was chosen mainly due to its high 45 C rating allowing for a higher discharge of electricity while still being lightweight and compact. This powerful battery easily satisfies the power demands of the Raspberry Pi, camera, 7.4V DC motor, and servo motor. Although the `Raspberry Pi 4B` runs off 5V, our Pi HAT contains a voltage regulator allowing the 7.4V output of the battery to be limited to 5V to power the Raspberry Pi. 

The wires of the battery are soldered to the circuits of the Raspberry Pi and ESC in parallel with a switch controlling the passage of electricity at the beginning of the circuit. This design eliminated the need for two separate batteries, saving space, simplifying our circuit, and reducing the car’s overall weight.

#### Potential Circuitry Improvements
Our switch is large and the wires connecting to it are too long. It extends the length of our car by a couple of centimeters, and its exposed nature is a structural weak point of the car. Our design could be improved by using a smaller switch with a shorter length of wire, making the car more compact. 

<img src="https://github.com/kylln20/WRO_FE_2023-24/blob/main/schemes/schematic.png" height="400px"> <img src="https://github.com/kylln20/WRO_FE_2023-24/blob/main/other/extra%20images/wiring2.jpg" height="400px"> 

### Sensors

For our sensors, we only use one camera to navigate both challenges. This was chosen over using LIDAR or adding ultrasonic sensors, as this helps to keep our power consumption as low as possible, keep our car and software design as simple as possible, and avoid more possible failure points. 

We use a `SainSmart Wide-Angle Camera`, which carries pixel data to the Raspberry Pi via a Camera Serial Interface (CSI) cable. We chose a CSI camera over a USB camera due to its low latency, high performance, low power consumption, and smaller size. Unlike a USB camera, the CSI camera has the drawback of not being hot-swappable, but overall, the benefits outweigh the cost.  The 'SainSmart Camera' also has a fish-eye lens which enables it to have a field of vision angle of 160 degrees, which allows us to detect more of the game field- whether that be the signal pillars, the coloured lines on the mat, or the walls- both at the front and to the sides of the car. The greater quantity of information allows the program to more accurately plan the car's movements.

Based on said pixel data, we can identify objects based on their size and colour. From such information, our program will calculate the desired speed and turning angle which it will send through the HAT to the DC and servo motors respectively with pulse-width modulation (PWM) signals. 

The camera uses a 5 MP OV5647 Sensor, which is adequate to detect basic colours for our needs, but has its limitations in different lighting conditions and distinguishing between similar colours

For the Canadian National WRO Future Engineers competition, the camera's sensitivity to different lighting conditions made it difficult to consistently run code that is unaffected by the environment and direction. Improvements we considered were changing the camera settings or attaching a lamp to the car to ensure consistent lighting. However, a solution was found by processing the colours using a different system (detailed in the Software section).

#### Potential Sensing Improvements
Although this system is sufficient for our needs, object detection can be further improved by using a camera with a higher-quality sensor such as the [Raspberry Pi HQ Camera M12](https://www.pishop.ca/product/raspberry-pi-hq-camera-m12/), which performs better in different lighting and can easily distinguish between colours. An improvement to the camera would help maintain consistency in the programs to an even higher degree.

Another possible improvement is the implementation of a `Gyro Sensor`, which tracks the car's orientation. We attempted to use a [BerryIMU](https://ozzmaker.com/product/berryimu-accelerometer-gyroscope-magnetometer-barometricaltitude-sensor/) for this function but decided against using it due to the extra complexity it added and its inconsistent readings. By tracking the car's orientation and keeping it heading at the same angle, it is possible to make parking more consistent and allow the car to control more precisely allowing it to go faster for the open challenge. 

An example of an alternative gyro sensor that may offer higher accuracy is the [BNO055 Absolute Orientation Sensor](https://www.pishop.ca/product/adafruit-9-dof-absolute-orientation-imu-fusion-breakout-bno055/)

&nbsp;

💻 Software 💻
===
We use a `Raspberry Pi 4 Board` as our single board computer (SBC). It is connected to the HAT, from which it takes and processes sensor input to return turning-angle and speed values back to the HAT, which then gets sent to the servo and DC motors respectively. 

The program running on the Raspberry Pi is written in Python.     

🛜 Initialization and Connection Process 🛜
---
We used the Raspberry Pi imager to write the Raspberry Pi operating system onto an SD card that allowed us to use our Pi HAT. Once the operating system is downloaded onto the SD card, when the Raspberry Pi is running AP (Access Point) mode, we can connect to the Raspberry Pi through wifi. Once we have selected the Access Point in the wifi tab, we use VNC Viewer to connect remotely to and interact with the Raspberry Pi using a set IP address. 

Object Management
---

### Object Detection <sub> (Open Challenge / Obstacle Challenge) </sub>

The camera captures an image, which the program then converts from OpenCV’s default pixel data format of BGR (blue, green, red) to `LAB (lightness, green-red, blue-yellow)`. We chose to use the LAB colour space because it performs better no matter the lighting environment. Previously, we used `HSV (hue, saturation, value)`. It was easier to select ranges for our colour masks than BGR or RGB. While LAB makes it less intuitive to find the colour ranges, the colour masks themselves are better for detecting the objects, as the two values concerning colour allow for better control than the H variable in HSV does. A significant improvement from the change is that the colour masks defined using LAB values have eliminated instances where the robot mistakes the magenta parking lot for being a red signal pillar.
```py
img_lab = cv2.cvtColor(img, cv2.COLOR_BGR2Lab)
```

Then, we perform a Gaussian blur on the image using the OpenCV library `GaussianBlur()` function. This smooths any edges in the image and removes small noise, making the overall shape of any obstacles easier to detect. 
```py
img_blur = cv2.GaussianBlur(img_lab, (7, 7), 0)
```
<img src="https://github.com/kylln20/WRO_FE_2023-24/blob/main/other/extra%20images/base.PNG" height="300px"> <img src="https://github.com/kylln20/WRO_FE_2023-24/blob/main/other/extra%20images/Gaussian_Blur.PNG" height="300px">

Then, `LAB thresholding` is applied, which checks if all pixels are within a certain LAB range. The resulting image has pixels within this range (areas of interest) as white, and everything else black. This is done with the OpenCV library `inRange()` function, where we specify the input image and a colour mask (range of LAB values).

```py
#LAB colour masks for all ranges, the first array represents the lower bound, and the second represents the higher bound
rMagenta = [[0, 171, 106], [255, 195, 135]]
rGreen = [[0, 45, 0], [255, 117, 153]]
rBlue = [[54, 124, 25], [148, 164, 121]]
rOrange = [[0, 163, 163], [255, 191, 204]]
rBlack = [[0, 109, 113], [59, 137, 150]]
```

The colour mask[^3] allows us to account for how lighting causes colour variation for the target object. Additionally, the input image can be modified with array splicing so we only search in a specific region of interest. By only searching in the region of interest, we also reduce the processing required for the car to produce a speed and angle value to send to the motors. This gives the robot time to analyze more images, which means more frequent decisions, and obstacles that can be avoided more efficiently. This improvement made after nationals and led to the car avoiding obstacles better. 

```py
img_segmented = img_lab[ROI[1]:ROI[3], ROI[0]:ROI[2]]

mask = cv2.inRange(img_segmented, lower_mask, upper_mask)
```

<img src="https://github.com/kylln20/WRO_FE_2023-24/blob/main/other/extra%20images/Threshold.PNG" height="300px">

Following the creation of a mask, we perform two other operations on it: 

- Erosion: this morphological operation finds and removes areas of noise in the binary (black and white) image
```py
cv2.erode(mask, kernel, iterations=1)
```
- Dilation: this morphological operation fills in any gaps in bright areas in the binary image
```py
cv2.dilate(mask, kernel, iterations=1)
```
<img src="https://github.com/kylln20/WRO_FE_2023-24/blob/main/other/extra%20images/Dilation.PNG" height="300px">

These operations ensure only pillars are detected and their shape is accurate. 

The bounded white areas can then be extracted as a list of contours within a specified region of interest.

```py
contours = cv2.findContours(mask, cv2.RETR_EXTERNAL,
    cv2.CHAIN_APPROX_SIMPLE)[-2]
```

We use this method of detection for all target objects including the signal pillars, the coloured lines on the game mat, the magenta parking lot, and the black walls around the track. This processing is placed in a function that takes in the LAB image, LAB mask ranges, and the ROI in which contours should be detected. The function returns a list of contours from the thresholded mask: 

```py
def find_contours(img_lab, lab_range, ROI):
```
In a separate function: 

```py
def max_contour(contours, ROI):
```

we measure the area of the specific contour using the OpenCV library function contourArea().

```py
area = cv2.contourArea(cnt)
```

The area is returned in an array with additional data as the x-coordinate, y-coordinate, and the contour object. 

#### Potential Object Detection Improvements

This algorithm is not perfect and the contour will not be perfectly aligned with the shape of the pillar, but it is sufficient for our needs. The accuracy of the object detection algorithm could hypothetically be improved with the use of even more morphological operations performed over more iterations. 

One approach we tried was to use a bilateral filtering algorithm to better retain the edges of the pillars,

```py
 cv2.bilateralFilter(image, d=9, sigmaColor=75, sigmaSpace=75)
```

but the program slowed from 30 fps down to 8 fps. If one could optimize the Raspberry Pi 4's performance or make our obstacle challenge code more efficient, these operations could be performed easily leading to more accurate object detection. 

[^3]: The colour masks used for each object still depend on the environment the car is in. We had difficulties getting the program to perform well in a room with yellow-tinted lights instead of white LEDs, especially before switching to LAB. This required changing the colour masks when running the car in that environment. An existing code that was useful for finding/adjusting colour masks was from an [OpenCV tutorial](https://docs.opencv.org/3.4/da/d97/tutorial_threshold_inRange.html), which was modified to be the ColourTesterLAB.py code.

### Wall Detection/Management <sub> (Open Challenge / Obstacle Challenge) </sub>

The wall contours are detected with one region of interest for each wall. 

The areas of each contour are added to their respective variable, leftArea for the area of the left wall and rightArea for the area of the right wall. 

In addition to the area of the black wall, we also add the areas of any magenta contour we see to help avoid collision with the parking lot. 

<img src="https://github.com/kylln20/WRO_FE_2023-24/blob/main/other/extra%20images/wallcontour.png" height="300px">

To stay centered when driving straight, we use a proportional derivative (PD) algorithm, which involves calculating the difference between the areas of the two contours and calculating a turning angle based on:

* A difference in contour areas (`error`)
* A straight constant (`straightConst`)- the number that would be sent for the car to go straight
* A proportional constant (`cKp`) - the constant that gets multiplied by `error` 
* A derivative constant (`cKd`) - the constant that gets multiplied by the difference in the error and the previous error (`prevError`)

The resulting calculation is:
```py
 angle = int(straightConst + error * cKp + (error - prevError) * cKd)
```
&nbsp;

### Signal Pillar Detection/Management <sub> (Obstacle Challenge) </sub>

In the Obstacle Challenge, if a signal pillar is detected, the program will switch from calculating the angle based on the walls to the signal pillar instead. 

Signal pillars are found with green and red colour masks, and by searching in a region of interest specific to the locations of the obstacles. 

<img src="https://github.com/kylln20/WRO_FE_2023-24/blob/main/other/extra%20images/pillarcontour.png" height="300px">

A function called `boundingRect()` approximates a rectangle around the selected contour. `boundingRect()` also returns the x and y coordinates of the rectangle’s top left corner. When applied to the contour of the signal pillar, this can be used to determine its location.

Then, a PD calculation is applied based on the difference between the x-coordinate of the pillar, and the target x-coordinate. The target x-coordinate for the green pillars is near the right side, as the car needs to pass it on the left side. The opposite is true for the red pillars. The calculation also includes a value changing the angle based on how close the pillar is by using the pillar's y-value. 

```py
#calculate error based on the difference between the target x coordinate and the pillar's current x coordinate
error = target x - current x

#calculate new angle using PD steering
angle = int(straightConst + error * cKp + (error - prevError) * cKd)

#adjust the angle further based on the y-coordinate (cy) value
angle -= int(cy * y) if error <= 0 else -int(cy * y)
```

<img src="https://github.com/kylln20/WRO_FE_2023-24/blob/main/other/extra%20images/pillarcoord.png" height="300px">

In the event there are 2 or more pillars seen, we determine which one to focus on by calculating the distance between the bottom-middle of the screen to the bottom-middle of the pillar. We use the closest pillar to calculate the servo angle. 

Additionally, we change the control variables to be weaker when 2 or more pillars of the same colour are seen, so the car can successfully navigate tight corner cases. 

While we detect a pillar, if the area of the left or right walls becomes too large, we deselect the current pillar so the wall areas determine the angle instead. This allows the car to turn towards the middle and avoid hitting the wall

After twelve turns, once the car has completed three laps and is searching for the parking lot, the target x-coordinate is such that the car drives toward the outside of the red and green pillars.

&nbsp;

### Turning <sub> (Open Challenge) </sub>
The car begins a turn when the area of either wall is below a certain threshold. It then turns in the direction of the wall with the lesser area.

```py
if leftArea <= turnThresh and not rTurn:
    lTurn = True

elif rightArea <= turnThresh and not lTurn:
    rTurn = True
```

During a turn, we set the servo to a default turning angle of 25 degrees (sharp left/right). However, if the angle calculated through the difference of wall areas is greater than 25 degrees and is below the absolute angle limit (max left/right), the car will use this angle instead of the default 25 degrees. This ensures we don’t hit the wall during tighter turns. 

```py
if lTurn:
    angle = min(max(angle, sharpLeft), maxLeft)
elif rTurn: 
    angle = max(min(angle, sharpRight), maxRight)
```

 The turning ends once the area of the side that was below the threshold regains enough area. Additionally, to count the number of corners the car has passed, the program tracks whether the orange or blue lines on the mat have been detected. The line is searched for using our object detection algorithm, with an orange colour mask on a centered region of interest. Once the area of the line contour has passed a certain value, the program knows the car has passed a corner.
 
```py
if (rightArea > exitThresh and rTurn) or (leftArea > exitThresh and lTurn): 
    end turn
    increase number of turns if orange or blue line was detected
```
&nbsp;

### Turning <sub> (Obstacle Challenge) </sub>
Unlike the open challenge, in the obstacle challenge, we can't detect turns by the areas of walls due to the need to avoid pillars at the entrance and exit of the turn. To compensate, the obstacle challenge code instead enters a turning mode once the nearest mat line (blue if travelling clockwise, orange if travelling counter-clockwise) has been detected and is of a certain area. 

The car is automatically set to the maximum 50-degree turning angle to ensure it can see pillars quickly after a turn. 

If it detects a signal pillar, the turn ends immediately, and the angle calculation is based on the signal pillar. Otherwise, like in the open challenge, the program will exit the turning mode when the difference between the two wall contours has decreased to a certain threshold, and the angle calculation will be based on the wall area difference.

If a pillar is detected during a turn, we found the car may struggle in certain cases to successfully turn around the pillar when the angle of approach is very narrow. To counteract this, we added a 5th region of interest for detecting the wall in front to turn earlier. If a turn is ended by seeing a pillar, we check if this region of interest is filled and turn to the maximum angle in the same direction as the car's turning direction even if we still detect the pillar. 

If the pillar's area becomes too large while turning, the car turns too early and is on course to hit. In this case, we straightened the car's turning angle until the area was lower than a certain threshold to avoid collision. 

```py
if ((ROI5_area > threshold and turnDir == left) or (ROI5_area > threshold and turnDir == right)):

    if pillar_area > threshold:
        turn_angle = straight
    else: 
        if turnDir == right:
            turn_angle = sharp_right
        else:
            turn_angle = sharp_left
```
<img src="https://github.com/kylln20/WRO_FE_2023-24/blob/main/other/extra%20images/ROI5.png" height="300px">

As we don't want this region of interest to interfere with our regular driving algorithms, the region of interest is only present when needed in tight cases where the area of the left wall area is large enough when starting a left turn or the right wall area is large enough when starting a right turn. 

```py
if (turnDir == right and orange_line_detected) or (turnDir == left and blue_line_detected): 
    if pillar_area > 0 and ((left_wall_area > threshold and turnDir == left) or (right_wall_area > threshold and turnDir == right)):
        show ROI5 and use it
```
            
The region of interest is then hidden once the camera no longer detects the wall in front, a pillar in front, or there is a large enough difference in the wall areas. 

```py
if (pillar_area == 0 and ROI5_area > threshold) or (wall_area_difference > threshold and ROI5_area > threshold):
     hide ROI5
```

This approach makes the car turn earlier making the turns around pillars much more consistent, allowing our car to control better at faster speeds. 

&nbsp;

### Parking Lot Detection/Management <sub> (Obstacle Challenge) </sub>
After three laps are completed, we set a timer of two seconds so we stop in the starting section, the car then moves to pass all pillars on the outside to make it easier for the car to park. 

During parking, ROI5 is always shown to make sure turns are as sharp and quick as possible for an easier approach while parking. 

The parking walls are found with magenta colour masks and by searching in two regions of interest that were used to detect walls, again with LAB thresholding. This starts after twelve turns. Any time after thirteen turns, parking mode will start after a magenta contour of the right size reaches a specific Y-coordinate in either of the regions of interest.

<img src="https://github.com/kylln20/WRO_FE_2023-24/blob/main/other/extra%20images/parkingdetection.png" height="300px">

Once the magenta parking lot has been found in the left or right region of interest, we delay using time.sleep() based on the detected area to ensure the car doesn't turn too early. 

```py
time.sleep((lot_area) / (constant))
```

After, the car turns to the direction in which the parking lot has been detected. If the program detects a magenta contour in the central region of interest, the car is not centered between the parking walls. To avoid hitting the walls, the car backs up to allow more distance to adjust. Additionally, while parking into the lot on the left, if the right region of interest is found to have a large enough area in both magenta and black, the car is too far left, meaning we have to turn right.
```py

if parking lot is on the right:
     
     if parking lot detected in front:
         back up while turning left
     else:
         turn right
 
 elif parking lot is on the left:
     
     if right wall area > threshold and right parking lot area > threshold:
         turn right
     if parking lot detected in front:
         back up while turning right
     else:
         turn left

if the area of the wall in front > threshold:
    turn the wheels straight and stop the car
```

The car stops once the area of the wall detected in the middle is large enough, using the same region of interest (ROI) that detects the orange/blue lines.

&nbsp;

### Three-Point Turn <sub> (Obstacle Challenge) </sub>

After the eighth turn has been counted by seeing a wall or a pillar, we check whether a three-point turn is required. This is done by checking whether there was a pillar directly in front of the car at the start of the program and the area of the pillar detected during the 8th turn. 

We determine if there was a pillar in front of the car in the starting section by seeing if the maximum pillar area we detected before the first turn is larger than a certain threshold or if two pillars of a single colour were detected before the first turn. 

```py
if orange line detected and turn direction == right or blue line detected and turn direction == left
  if turns == 0 and pillarAtStart == not set:
     if largest pillar area > threshold:
         pillarAtStart = True
     else:
         pillarAtStart = False

if num_pillars_g >= 2 or num_pillars_r >= 2 and pillarAtStart == not set:
    pillarAtStart = True
```

If there was no pillar directly in front of the car in the starting section, we can assume that any pillar seen during the 8th turn is the last pillar of the second lap. 

If a pillar was directly in front of the car (in the starting section), we know it could not be the last pillar of the second lap. If there is another pillar in the starting section, it would be considered the last pillar in the second lap. If this extra pillar is present, it would be close to the edge as it's impossible to have a pillar in the middle with two pillars. This means that the area of the pillar that is seen during the turn must be large. Therefore, we check if the area of the pillar is above a threshold. 

If no pillar is detected during the 8th turn, the last pillar detected is the last pillar of the second lap so we use it to determine whether to do a three-point turn. 

```py
if turn is ended by seeing the wall: 
     if last pillar seen is red: 
          perform three-point turn
          
if turn is ended by seeing the pillar: 
     if there was a pillar directly in front: 
          if area of current pillar is larger than a threshold and is red: 
                 perform three-point turn
     if there was no pillar directly in front and current pillar is red: 
          perform three-point turn
```

This approach to determining the need to perform a three-point turn proved much more consistent than our last approach, which relied heavily on specific wall area and pillar area thresholds vulnerable to lighting and colour. 

Once we know a three-point turn must be performed, the car will immediately turn to the left unless it detects a red pillar, in which case it will turn after passing the red pillar by waiting until no pillar is detected or the area of the wall in which the car is turning towards is large enough. The car will turn left until it detects the wall or parking lot in front using the same ROI used for detecting the coloured lines. It will then back up while turning to the right for a certain period. Then the program will resume.

After the initial three-point turn, if the car detects a large black area in front again, the initial three-point turn isn't sharp enough, so another three-point turn is performed.

If the car doesn't detect the wall in front and instead comes too close to a pillar, it means the car has already turned around, so we count an extra turn.

### Backing Up <sub> (Obstacle Challenge) </sub>

In certain cases where the car may not be able to pass a pillar without moving it, the car will move back. We determine when the car will move back by checking the area of the current selected pillar and its distance from its target x-coordinate

```py
if pillar area > threshold and current x-coordinate is far from its target x-coordinate:
    move back 
```

### Potential Improvement: Stuck Detection <sub> (Open Challenge / Obstacle Challenge) </sub>

In our testing, very rarely our car would get stuck on the wall and not be able to move. Although this happens such a small percentage of the time, having a method to counteract this would be good to have. 

One method we considered to check for when we were stuck was comparing the camera image changes and seeing if they were similar. We decided against its implementation due to the rarity of becoming stuck and our time constraints. 

This could be implemented with two methods: 

1. Mean Squared Area (MSE): measures the average squared difference between the pixel values of the two images.
2. Structural Similarity Index (SSIM): a scikit-image method that offers a more accurate comparison at the cost of speed.

To use SSIM download the scikit-image library through the Raspberry Pi terminal: 

```py
sudo pip install scikit-image
```

Here's an implementation of both methods: 

```py
import cv2
from skimage.metrics import structural_similarity as ssim
import numpy as np

def mse(image1, image2):
    # Compute the Mean Squared Error between the two images
    err = np.sum((image1.astype("float") - image2.astype("float")) ** 2)
    err /= float(image1.shape[0] * image1.shape[1])
    return err

# Load the two input images
imageA = cv2.imread('path/to/first/image.jpg')
imageB = cv2.imread('path/to/second/image.jpg')

# Convert the images to grayscale
grayA = cv2.cvtColor(imageA, cv2.COLOR_BGR2GRAY)
grayB = cv2.cvtColor(imageB, cv2.COLOR_BGR2GRAY)

# Calculate MSE and SSIM
m = mse(grayA, grayB)
s, diff = ssim(grayA, grayB, full=True)

# Print the results
print(f"MSE: {m}")
print(f"SSIM: {s}")
```

To ensure these stuck detection methods don't interfere with the regular Obstacle Challenge algorithm, we can make it run in parallel using multi-threading. 

Implementation with the Python threading library: 

```py
import threading

def stuck_detect():
    while True:
        #implement stuck detection here

# Create a new thread
thread1 = threading.Thread(target=stuck_detect)

# Start the new thread
thread1.start()

#continue with obstacle challenge program
```

&nbsp;

🔨 Complete Assembly Instructions 🔨
===

1. **Strip the `Carisma GT24` chassis.**
   - The car itself comes with a realistic car cover. This is purely cosmetic and can be removed, along with the mounts supporting it.
   - The electrical components are housed within the center of the chassis. They can be accessed by unscrewing another plastic cover
     
2. **Removing unnecessary parts**
   - Take out the DC motor, servo motor, ESC, and RC module. The first three parts listed will be replaced by higher quality components.
   - This will require unscrewing as well as ripping parts off of the adhesive
   - Note that some rear portions of the car will need to the disassembled temporarily to access some screws

3. **Install the new parts**
   DC Motor Installation:
   - Install the `Aluminum DC Motor Mount`
   - Install The `Furitek Micro Komodo Brushless Motor` onto the motor mount
   - The motor gear may need to be replaced. Judge this based on how well it meshes with the drive system gears
   Servo Motor Installation: 
   - 3D-print our servo attachment, place it on the head of the servo motor, and secure it with a screw and nut. 
   - The `Hitec HS-5055MG Servo Motor` also needs its wings clipped before installing

5. **Wiring**
   - Ensure everything is wired properly, according to the schematic above.
   - Here, you can also splice your switch into your battery wires
   - Although they haven't been installed yet, you can test the connection to the Raspberry Pi and the battery
   - Although the Raspberry Pi and ESC both contain switches, we only use our self-added switch to turn on the whole system
   - 3D print a `cable barrier` and attach it onto the chassis to prevent cables from interfering with steering

6. **3D Printed Parts**
   - Print a base and a camera mount. Our designs can be found in this repository.
   - Note that our base was designed to fit smoothly on top of the chassis with the holes matching the 4 posts of the chassis
   - The camera screws onto the camera mount at the top where 4 small holes are present
   - The camera mount attaches by inserting it into the rectangular slots on the rear of the car base
   - These new parts provide housing for the camera, Raspberry Pi, Raspberry Pi Fan, and battery
   - The Raspberry Pi HAT fits nicely on top of the Raspberry Pi, secured and connected through the GPI0 pins

9. **Configuration**
   - Download the [Raspberry Pi Imager](https://www.raspberrypi.com/software/)
   - With the imager, prepare your MicroSD card and copy the [TurboPi OS](https://drive.google.com/file/d/1sBCMegKXQaT8nuhjBM0KjXP2YUlaAOju/view). Then, insert the card back into the Pi
   - Power on your Raspberry Pi. By default it is running in Access Point (AP) mode meaning you have to connect via a Wifi Access Point.
      - Search for a Wifi connection with the format: `HW-xxxxxx`
      - It will have a password of `"hiwonder"`
   - Remotely access your Raspberry Pi through [VNC Viewer](https://www.realvnc.com/en/connect/download/viewer/) by entering the IP address `192.168.149.1`
   - VNC Viewer will ask for a username + password
      - Username: `"pi"`
      - Password: `"raspberry"`
   - Now you can access your Raspberry Pi

10. **Load source files**
   - Go to the folder: /home/pi/TurboPi/HiwonderSDK and add the files found in `src`
   - For this competition, you also need to `auto-run` your program
   - Open the Pi terminal and run `sudo nano /etc/rc.local`
   - Add the program `(ObstacleChallengeV2.py/OpenChallenge.py)` with `sudo bash -c 'sudo python3 /home/pi/<<directory>>/<<filename.py>>' &`, before the line `exit 0`
   - Save and reboot
   - On start-up, the file placed in the rc.local file will run automatically
     
9. **Congratulations! You've built our robot!**
    - You can try running the `src` files directly from the Pi terminal using sudo python3 <<filename.py>> while in the right directory to run our program
    - You can use `Thonny`, a pre-installed compiler on the Raspberry Pi, as a code editor for the programs
    - Any other information can be found on this repository
    - Thanks for reading!

&nbsp;
   
     
