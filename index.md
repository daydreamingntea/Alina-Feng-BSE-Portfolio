# Project Name Here
Replace this text with a brief description (2-3 sentences) of your project. This description should draw the reader in and make them interested in what you've built. You can include what the biggest challenges, takeaways, and triumphs from completing the project were. As you complete your portfolio, remember your audience is less familiar than you are with all that your project entails!


| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Alina F | Lynbrook High School | Still Exploring | Rising Sophomore

(Alina F.heic)
  
# Final Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/F7M7imOVGug" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your final milestone, explain the outcome of your project. Key details to include are:
- What you've accomplished since your previous milestone
- What your biggest challenges and triumphs were at BSE
- A summary of key topics you learned about
- What you hope to learn in the future after everything you've learned at BSE



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

# Starter Project

<iframe width="560" height="315" src="https://www.youtube.com/embed/pxxaiZzEqbY?si=YBfAkAmAtdKXfj1w" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

The weevil eye uses a photoresistor (adjusts resistance inverse to the amount of light), a transistor, three resistors, and two LEDs. When less light is detected by the photoresistor, its resistance spikes and forces more current into the transistor. Once a threshold is met, power may flow and turn on the LEDs. A battery holder is present on the bottom of the weevil eye. 


# Schematics 
Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resoruces to create professional schematic diagrams, though BSE recommends Tinkercad becuase it can be done easily and for free in the browser. 

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
| RGB LED | 2 | switches colors while lighting up, decorative purposes | $8.99 | <a href="amazon.com/EDGELEC-Tri-Color-Multicolor-Diffused-Resistors/dp/B077XGF3YR/ref=sr_1_3?channelId=500&clpRedir=Y&dib=eyJ2IjoiMSJ9.BU4S0jVgvYFMaG3YX-8kv1-vTtV1-4Gj3Hi14qSCx07ecsaGTDoA1Hxw0Fg6sGxubCpTxWGF42A8j1evBEgIvH_FlcmgyidZiEnOakrQta6QfwOnnl-ZQOHwG3TMUHtETFsTPO4UKFgpdhWi1_AsiILIepaAREjx9IWxz-zxf1RYDV50_9qySpUzZljrQC5cbYliQJ-TfgFzZcfSxYTzP_A3s6ooSxL9QfiVliMQWK0.mG1exndiac7e2Czayq2kQDl7GdEQZWy7eeEvsmS-dVs&dib_tag=se&keywords=rgb+led&plpRedirect=mhFallback&qid=1784306996&sr=8-3"> Link </a> |
| blue LED | 2 | connected to pin 13, flashes when IR receiver gets a signal |  |  |
| white LED | 2 | behaves similar to a car's turn signals |  |  |
| ultrasonic sensor (HC-SR04) | 1 | detects distance via echolocation |  |  |
| IR obstacle avoidance module | 2 | detects nearby objects by emitting and receiving IR light |  |  |
| passive piezo buzzer | 1 | produces sound and is able to change pitch |  |  |
| shift register (74HC595) | 1 | expands number of digital output pins |  |  |
| resistors (330Ω, 1kΩ, 2kΩ, 5kΩ) | 2, 4, 2, 2 respectively  | prevent components from getting damaged |  |  |

# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

To watch the BSE tutorial on how to create a portfolio, click here.
