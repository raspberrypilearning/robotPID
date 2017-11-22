## Introduction

There is more to making a robot go in a straight line than just turning the motors on full power – in this tutorial you’ll learn how to add encoders to your robot and implement a PID controller to regulate the power.

Anyone who has ever built a wheeled robot will know that driving in a straight line is a lot more difficult than you first think. Sure, holding a true heading for 1, 2 or maybe 3 metres is possible, but keeping it up past 10 or 20 metres without a veer to the left or right becomes astonishingly tricky. 

There are many reasons why this happens – uneven surfaces, differences in wheel size, bent axles and, most significantly, the fact that no two motors turn at the same speed! Minor differences in manufacturing and materials result in minor differences in output, and as a result, one motor will spin more quickly than the other. This difference may well be very small, but over time (or distance), it will show as your robot beginning to veer. If the right motor is moving quicker, your robot is going to turn in an arc to the left, and vice versa.

To counter this problem, a solution is required that can accurately measure how fast each motor is moving and then use this feedback to adjust the motor’s speed at run-time so that each motor spins at the same rate.

Encoders are typically used to measure motor speed; these devices provide an output (or pulse) multiple times per revolution.

A PID (proportional-integral-derivative) controller is then used to continuously monitor and adjust motor speed to keep them in sync.

This tutorial steps through adding encoders to a Raspberry Pi-powered robot, using Python to create a PID controller, tuning it to work with your robot, and using the GPIO Zero (gpiozero.readthedocs.io) library to interact with the hardware.

![Going Straight] (images/PID Robot.png)