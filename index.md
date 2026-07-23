# Human Pestering Robot
This little robot I created can be driven via remote, has several obstacle avoidance systems, can follow objects, play a sound, and light up. Majority of these functions were added to make the robot appear approachable and enable it to midly annoy others. Ironically, I ran into many annoyances while designing and testing this robot.

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Alina F | Lynbrook High School | Still Exploring | Rising Sophomore

<img width = "3024" height = "4032" src = "Alina-F.png">

# Key Takeaways

During my time at BlueStamp, I expanded on my existing knowledge of the Arduino and circuit design. I had worked with sensors and components that I wasn't familar with. On top of that, I had to code in order for everything to work. Learning to code is something that I always despised and I certainly did not want to learn how to code just for this project. I ended up using Claude to write out the base code (since I am not familar with the format of coding) before making changes myself. Everytime a problem arose, my first instinct is to isolate certain variables and narrow down the issue (this method has served me well in this project). As for other skills I gained, I also learned to create schematics in Tinkercad and Fritzing (plus figuring out how to download Fritzing from Github). For the future, I hope to expand my knowledge of circuit components and familiarize myself with the art of problem solving.  
  
# Third Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/ZbtA5DcNpWU?si=88WjiowESC8bPYQ6" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

In this third milestone, I added back the sensors that were previously removed (IR obstacle avoidance, HC-SR04 ultrasonic sensor, line tracking). I was debating about removing the line tracking module since it would open up more digital pins that I could use for other components (LEDs and piezo buzzer). I spent some time playing around with the layout of the LEDs before deciding I wanted to add two RGB LEDs. At first, I had them connected to the analog pins and gave them a code so that they will continously change color once turned on. The code has each hue choose randomly between 0 and 255. Occasionally, all the values land on 255 which results in the LED appearing off. I was considering altering the code so this doesn't happen, but decided against it since I was already satisfied with how it worked. Two white LEDs were added to function as the car's turn signals. When a button for the car to turn is pressed, the corresponding LED will be set to true and the other will be false. 

After wiring the sensors, I began to play around with each one individually before combining everything into one code. This phase consisted of many frustrations as the sensor would appear to not be working or detecting anything. I added in multiple serial printing functions so I could see if the sensor was detecting anything at all in the serial monitor. After that, I find out if the issue was in the software or hardware. For the IR obstacle avoidance modules, I had a software issue and adjusted the code so the sensor would get priority over the other functions in the car when the sensors were active. As for the ultrasonic module, I connected the ground and power wires into a different area on the breadboard. 

When it came to testing the robot using the combined code (this includes all the sensors and LEDs), the car would not be able to drive at all but I could hear the motors attempting to turn. Perhaps the motor controller was taking up too much power, so a seperate battery was added for the motor controller (this consisted of three AAA batteries) and I had the 9V battery replaced. This did allow the car to drive normally but the motor controller would overheat. The second battery was removed and the motor controller stopped overheating. Thankfully the car was still able to drive normally since the old 9V battery was replaced. 

Unfortunately, the Arduino did not have enough digital pins for the next two components I wanted add: a passive piezo buzzer and a LED connected to pin 13 (the LED will light up everytime the IR reciever gets a signal from the remote). I began to research different components that would expand the number of digital pins available before settling on the 74HC595 shift register (which came with this kit). Since the half sized breadboard was already a bit crowded, I put the shift register on a mini breadboard instead. This way I could also avoid having to rearrange components on the half sized breadboard. The shift register requires connections to three digital pins on the Arduino and opens up eight more digital pins, but the pins on the shift register are not PWM pins nor input pins. I decided to rearrange the pin connections so I could have the two white LEDs and one RGB LED on the shift register and move one of the pins from the ultrasonic sensor to an analog pin along with the piezo buzzer. The three pins from the shift register are connect to pins 2, ~3, and 4. Moving the white LEDs also opened up pin 13, so I chose to connect two blue LEDs to that pin with LED feedback enabled. Now, when the IR receiver gets a signal, they will light up. For some reason, the pins on the shift register do not match their function (e.g. Q0 needs to be defined as 2 in order for the component to function). I spent time doing some trial and error in order to figure out which ones needed to be redefined for the components to work.

# Second Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/7uoHsh0dZ4o?si=JFxf60nT4T1G4ZaD" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

In this milestone, the mini breadboard was removed in favor of using a half-sized breadboard to give myself more room for any components I may add in the future. I used velcro to attach the half-sized breadboard for easy relocation. Majority of the sensors and modules have been removed as I did not plan on using them (obstacle avoidance module, ultrasonic sensor, and line tracking module). As of right now, the only component on the breadboard is a 38kHz IR receiver. The receiver is able to detect IR signals from the remote and converts that into electrical commands. Receivers use photodiodes to absorb light along with a filter to ensure that only IR waves may pass through. For the wiring, one leg is wired to GND, another is wired to the 5V pin on the Arduino, and the last is wired to digital pin 12. The VCC pin from the motor controller is connected to the VCC leg on the receiver (and also the 5V pin). 
  
The code requires installation of the IRremote library. When a button is pressed on the remote, the receiver will detect which button is pressed and carry out the corresponding action. Movement functions set the four motor pins using PWM, with pin combinations that determine the wheels' direction of rotation, enabling the car to move foward, backward, left, right, and spin in place. A decoding function is used to convert the receiver's signals so it is easily readable and ignores any unrecongnized signals. 
  
The first issue I had encountered was my computer being unable to upload code to the Arduino (even though the correct board and port was selected). I tried swapping out USB cables, adapters, and ports but nothing had changed. Eventually, I decided to borrow another computer to upload code for the time being. After I went back and changed a few settings in the Arduino IDE, I was able to upload code. While testing the remote, I noticed that the robot had a tendency to drift right when it went forward or backward. A code for speed calibration was added so the wheels could spin at the same rate. The EEPROM library was added so the Arduino could preserve any speed calibrations when powered off. Since the left wheel was spinning faster than the right, the speed of the left wheel was reduced to 91% of the right wheel's speed. A helper function was added to keep the robot's speed between 0 and 255. 

# First Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/BZBUk8scZYY?si=7nvxbyhpaTeg-iDW" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

The robot uses an acrylic plate as a base where the other parts will reside. On the top, an Arduino Uno is fastened using standoffs and screws, this will read inputs and translate them into outputs. A mini breadboard is attached anterior of the Arduino. The breadboard will be used to prototype, build, and test any circuits I plan on creating in the future. As of now, an ultrasonic sensor is attached to its front end and may be used to measure distance via echolocation (this can be used to automate the robot). Similarly, the two IR observance modules (these are screwed onto the left and right anterior ends of the acrylic plate on the topside) can function as proximity sensors by utilizing IR light. A line track module screwed to the bottom front side of the acrylic plate enables the car to navigate along a designated line. 
  
On the bottom of the acrylic plate, two motors are mounted with two TT wheels attached. Behind them is the universal wheel that has been mounted using standoffs and screws. The wheel is able to rotate 360º, providing the car with extra mobility and balance. Between the two motors is the 9V battery that has been attached using velcro. All the wires from the motors and battery's snap connector is threaded through a hole anterior of the universal wheel so they are easily accessible from the plate's topside. This way, the wires from the motor may be connected to the L9110 module (the car's motor controller) and the battery can be connected to the Arduino Uno. 

Basic wire setup for the car has also been completed in this milestone. The wires from the TT motors has been connected to the motor controller and is secured using screws. Jumper wires connect the pins from the motor controller to the Arduino, this will enable the wheels to rotate and move the car. Pins A-1B, A-1A, B-2A, and B-1A are connected to digital pins 5, 6, 9, and 10 respectively. These pins are responsible for the wheels' direction of rotation and thus, the direction the car drives in. 

As for why I chose this project, I wanted to expand on my Arduino knowledge and familiarize myself with other circuit components. This project is relatively simple and did not require the use of hazardous tools, which meant that I have extra time and room to add my own modifications while staying safe. Plus, I could design this robot to pester my friends and family (this is the internal motivation for doing this project). 

# Starter Project

<iframe width="560" height="315" src="https://www.youtube.com/embed/pxxaiZzEqbY?si=YBfAkAmAtdKXfj1w" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

The weevil eye uses a photoresistor (adjusts resistance inverse to the amount of light), a transistor, three resistors, and two LEDs. When less light is detected by the photoresistor, its resistance spikes and forces more current into the transistor. Once a threshold is met, power may flow and turn on the LEDs. A battery holder is present on the bottom of the weevil eye. 


# Schematics 

Note: The color coding on the schematic is to help distinguish the wires of different components and the colors may not match with the ones on the robot itself, some wires are striped to help differentiate between wires of other components along with ground and power. This schematic uses a L293D motor driver to mimic the wire placement on the L9110 motor driver since it could not find it in Fritzing.

Breadboard view:
<img src="https://github.com/user-attachments/assets/d29946c2-08b1-4d49-9d20-120fcfc3a707" alt="annoy_ppl_bb" style="max-width: 100%; height: auto; display: block;" />

Schematic view:
<img src="https://github.com/user-attachments/assets/1de8e15e-7df2-4925-923c-9a0101b8218f" alt="annoy_ppl_schem" style="max-width: 100%; height: auto; display: block;" />

PCB view:
<img src="https://github.com/user-attachments/assets/054297fc-252f-4239-ac55-eb5604067436" alt="annoy_ppl_pcb" style="max-width: 100%; height: auto; display: block;" />

# Code
Here's where you'll put your code. The syntax below places it into a block of code. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize it to your project needs. 

```c++
void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  Serial.println("Hello World!");
}

void loop() {
  // put your main code here, to run repeatedly:

}
```

# Bill of Materials
The 3 in 1 kit from SunFounder includes most of the parts used in this project. Parts that came with the kit will not have their price nor their link listed while parts not included in the kit will have both the price and link listed.

| **Part** | **Amount Used** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|:--:|
| 3 in 1 kit | 1 | kit includes majority of the materials used to build the car | $69.99 | <a href="https://www.sunfounder.com/products/sunfounder-3-in-1-iot-smart-car-learning-ultimate-starter-kit"> Link </a> |
| acrylic plate | 1 | main body for components to reside on, structural support |  |  |
| Arduino Uno R3 | 1 | reads inputs, proccess data according to code, control outputs  |  |  |
| 9V battery| 1 | power supply |  |  |
| 9V battery cable | 1 | connects battery to the Arduino |  |  |
| L9110 motor driver | 1 | control speed and direction of motors |  |  |
| TT motor | 2 | convert electrical energy into mechanical energy to drive wheels |  |  |
| TT wheel | 2 | rotates to drive the car |  |  |
| 1" universal wheel | 1 | third wheel for balance, can rotate 360º |  |  |
| IR remote control | 1 | operates the car and sends binary code to a receiver |  |  |
| IR receiver | 1 | receives the signal from the remote |  |  |
| half sized breadboard | 1 | most components reside here | $6.99 | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/](https://www.amazon.com/DEYUE-breadboard-Set-Prototype-Board/dp/B07LFD4LT6/ref=sr_1_5?channelId=500&clpRedir=Y&dib=eyJ2IjoiMSJ9.OVjKxIeCVYNU10JQfr5F6xG-vHw-BjGUMjXarhDZV6SfhzbbpyaLfDx_YoTfuRBtDvoFgI-O5RlwoAqxruW54kUgKCosnFw5PookczumSEHN2fcG7ZeMO9YrkjcHO3aWHbNMuQi7pYNXyFRjS53Y4_u7lJ-aOkHyATjjMtCrb6KcX259wK7Mi7Ga6uZtbhsHRciS18MbzilPQVByR2iMDUFpIh1_X7u-zzdJBs1TWPc.B_gI1SvrzH61RVDUf6cZuoKmMHZL_0IK8kogO8hVMtQ&dib_tag=se&keywords=half+size+breadboard&plpRedirect=mhFallback&qid=1784306456&sr=8-5"> Link </a> |
| mini breadboard | 1 | extra space for wiring components |  |  |
| RGB LED | 2 | switches colors while lighting up, decorative purposes | $8.99 | <a href="https://www.amazon.com/EDGELEC-Tri-Color-Multicolor-Diffused-Resistors/dp/B077XGF3YR/ref=sr_1_3?channelId=500&clpRedir=Y&dib=eyJ2IjoiMSJ9.BU4S0jVgvYFMaG3YX-8kvy2xEtIibcREs2Owe4pu8svyOM3ehUqVvSHt-sFyBsmkBMaGC6Uhf6J-7nHvDBNUjJ-ewEEmlnBGY0Esf2tksDMXRcH7JOQWpuymyKSwyCoBVNRiUFmKrw2g4wmVlvbNRl4lZV5sBrx12FNHWpruY-rORlUMc2JnJ3vSiGQ9fvvNqMRtwxPXCC2YcUfRZtMZZT_4tsFLBs_Y4XGW_AKSsBE.vvlrNAq1Et4AUnl-VssLzH9y_bMpm10NB2Ykm0r7l9g&dib_tag=se&keywords=rgb%2Bled&plpRedirect=mhFallback&qid=1784572999&sr=8-3&th=1"> Link </a> |
| blue LED | 2 | connected to pin 13, flashes when IR receiver gets a signal |  |  |
| white LED | 2 | behaves similar to a car's turn signals |  |  |
| ultrasonic sensor (HC-SR04) | 1 | detects distance via echolocation |  |  |
| IR obstacle avoidance module | 2 | detects nearby objects by emitting and receiving IR light |  |  |
| passive piezo buzzer | 1 | produces sound and is able to change pitch |  |  |
| shift register (74HC595) | 1 | expands number of digital output pins |  |  |
| resistors (330Ω, 1kΩ, 2kΩ, 5kΩ) | 2, 4, 2, 2 respectively  | prevent components from getting damaged |  |  |
| jumper wires (M-M & F-M) | 20 & 12 respectively | create electrical connections |  |  |
| screws (M3x6mm & M2.5x6mm)  | 22 & 8 respectively | fasten components |  |  |
| nuts (M3) | 6 | fasten components |  |  |
| standoffs (M3x24mm, M3x12mm, M2.5x11mm) | 4 each | elevate certain components |  |  |
| velcro (1 in strip) | 2 | attach components while allowing for easy removal |  |  |
| screw driver | 1 | screwing in screws, adjusting potentiometers |  |  |
| USB-A to USB-B cable | 1 | connect Arduino to computer |  |  |
| USB-B to USB-C adapter | 1 | connect the cable to computer port | $6.99 | <a href="https://www.amazon.com/Syntech-Adapter-Thunderbolt-Compatible-MacBook/dp/B07CVX3516/ref=sr_1_3?channelId=500&clpRedir=Y&dib=eyJ2IjoiMSJ9.d7LKMhCLqwSoIHvDHsmfNNASCcVrrSwIS4h1KNDXWaRlfv0Af9ia70iXoIl6q9XTGAAwQLY_Mqrql2JI0XznGBRShN8fWvmudbknWJjx-Cap4A_2fsLNIYGaT3qJ5T9uXpjI_nG7pi_OTwSYGeLWBtEhwgsFeNQeNk24qXI_nkghOiFOH-1DVKolZwrI3KQOInaAGnf8V-C1FKPEwEY_bQyMn8Fk7zb5oI00bNkg9fk.HC8ik8XHZQiflxFCElxXHv1JYhxPqz-lKOqaUxmfI1k&dib_tag=se&keywords=usb%2Bb%2Bto%2Busb%2Bc%2Badapter&plpRedirect=mhFallback&qid=1784572867&sr=8-3&th=1"> Link </a> |

# Remote Control

Below is the layout of the IR remote used for this robot. I included the names of each button based on their names in the code along with their function.

| | | |
| :--- | :---: | ---: |
| **Power** (lock all other buttons)| **Mode** (+500Hz for buzzer) | **Mute** (-500Hz for buzzer) |
| **Play/Pause** (play R2D2 sounds) | **Backward** (enable IR obstacle avoidance) | **Forward** (enable ultrasonic sensor) |
| **EQ** (follow an object) | **Minus** (-25 speed) | **Plus** (+25 speed) |
| **0** (stop any non-numbered commands) | **Cycle** (play buzzer) | **U/SD** (self-driving mode) |
| **1** (turn left front) | **2** (drive forward) | **3** (turn right front) |
| **4** (rotate counter clockwise) | **5** (enable RGB LED) | **6** (rotate clockwise) |
| **7** (turn left back) | **8** (drive backward) | **9** (turn right back) |
| | | |

**A few things to note:**
 - pressing POWER once will lock all other buttons, pressing it again will unlock
     - pressing POWER will also terminate any already running commands
 - pressing + too many times will not cause the car greatly increase in speed
     - speed is capped at 255
     - car will not be able to drive once speed is at 100 or lower
 - if PLAY/PAUSE is pressed while CYCLE is running, the R2D2 sound will play
     - buzzer sound will resume once R2D2 sound is completed
 - buttons may be continously pressed to run a command
  
# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

To watch the BSE tutorial on how to create a portfolio, click here.
