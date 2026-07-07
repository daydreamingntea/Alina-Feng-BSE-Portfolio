# Project Name Here
Replace this text with a brief description (2-3 sentences) of your project. This description should draw the reader in and make them interested in what you've built. You can include what the biggest challenges, takeaways, and triumphs from completing the project were. As you complete your portfolio, remember your audience is less familiar than you are with all that your project entails!


| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Alina F | Lynbrook High School | Still Exploring | Rising Sophomore

**Replace the BlueStamp logo below with an image of yourself and your completed project. Follow the guide [here](https://tomcam.github.io/least-github-pages/adding-images-github-pages-site.html) if you need help.**

![Headstone Image](logo.svg)
  
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
  The code requires installation of the IRremote library. When a button is pressed on the remote, the receiver will detect which button is pressed and carry out the corresponding action. 
  
- Technical details of what you've accomplished and how they contribute to the final goal
- What has been surprising about the project so far
- Previous challenges you faced that you overcame
- What needs to be completed before your final milestone 

# First Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/BZBUk8scZYY?si=7nvxbyhpaTeg-iDW" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

  The robot uses an acrylic plate as a base where the other parts will reside. On the top, an Arduino Uno is fastened using standoffs and screws, this will read inputs and translate them into outputs. A mini breadboard is attached anterior of the Arduino. The breadboard will be used to prototype, build, and test any circuits I plan on creating in the future. As of now, an ultrasonic sensor is attached to its front end and may be used to measure distance via echolocation (this can be used to automate the robot). Similarly, the two IR observance modules (these are screwed onto the left and right anterior ends of the acrylic plate on the topside) can function as proximity sensors by utilizing IR light. A line track module screwed to the bottom front side of the acrylic plate enables the car to navigate along a designated line. 
  
  On the bottom of the acrylic plate, two motors are mounted with two TT wheels attached. Behind them is the universal wheel that has been mounted using standoffs and screws. The wheel is able to rotate 360º, providing the car with extra mobility and balance. Between the two motors is the 9V battery that has been attached using velcro. All the wires from the motors and battery's snap connector is threaded through a hole anterior of the universal wheel so they are easily accessible from the plate's topside. This way, the wires from the motor may be connected to the L9110 module (the car's motor controller) and the battery can be connected to the Arduino Uno. 

  Basic wire setup for the car has also been completed in this milestone. The wires from the TT motors has been connected to the motor controller and is secured using screws. Jumper wires connect the pins from the motor controller to the Arduino, this will enable the wheels to rotate and move the car. Pins A-1B, A-1A, B-2A, and B-1A are connected to digital pins 5, 6, 9, and 10 respectively. These pins are responsible for the wheels' direction of rotation and thus, the direction the car drives in. 


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
Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |

# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

To watch the BSE tutorial on how to create a portfolio, click here.
