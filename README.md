<div align="center">
    <h1 id="Header">Autonomous-R/C Car Hybrid System</h1>
</div>

## Overview

This is Robotic Car Model with two control modes: Autonomous Control Mode and Remote Control Mode (Default). In the Autonomous Control Mode, car drives forward until it detects an obstacle at which point it stops and changes 
direction. Or, if we push the button, the car switches modes to  Remote Control Mod and responds only to commands given to it from the Java program. The car also contains an LED to indicate which mode it is in and a power switch to turn the whole thing on or off.

<div align="center">
    <img src="Autonomous-Car.png" alt="screenshot" width="400px" height="300px">
</div>

## Technologies/Tools Used
* Hardware: Arduino, Ultrasonic Sensor, LEDs, Motors, Power Switch
* Languages: Java, C++ (Arduino IDE)
* Communication: Serial Communication between Arduino and Java
* Techniques: Non-blocking delta timing, Finite State Machine (FSM)

## Serial and Remote Control Communication
One of the most essential points of this project was establishing serial communication between the Arduino and a Java program running on the laptop. Serial communication provides a simple and efficient way to transmit data between the Arduino and a Java program running on the laptop over a physical connection; it enables real-time control and data exchange between the car and the computer. This communication allows the Java program to send control commands to the Arduino, such as directing the robot to move forward, backward, turn left, or turn right. Additionally, it enables Arduino to send back important information, such as sensor readings and status updates, which can be used by the Java program to monitor the car's environment and behavior. So, to achieve this, I established a protocol in Java to send a variety of meaningful messages one byte at a time. Then, I used this protocol to control (or not control!) a robotic car from a Java program and send useful data about the car's location back to Java.

## Autonomous Control Mode
The Autonomous Control mode involves the car continuously monitoring its surroundings using an ultrasonic distance sensor. When the sensor detects an obstacle within a certain range, the car initiates a sequence to avoid the obstacle by backing up and then turning in a new direction. This behavior allows the car to navigate its environment autonomously, reacting to obstacles in real-time to avoid collisions.

## Remote Control Mode
In the Remote Control mode, I have implemented a non-blocking delta timing, a practical technique, to control the timing of the car’s various outgoing messages. This technique equips the car with the ability to process incoming messages and determine its distance from obstacles in a non-blocking manner, enhancing its overall efficiency. I also implemented an FSM with four states (idle, receiving, move, moveFor) for moving the car, then defined the commands for moving the car: f (forward), b (back), l (left), and r (right), whichever distance was sent from the incoming messages.
