## Proportional control

Proportional control is adjusting the motor speed by adding the value of the error – the value of the error (the difference in encoder ticks between the target and the actual speed) will need to be converted to the motor speed (a value between 0 and 1) by multiplying a constant (KP) to get a ‘proportional’ change:

**adjustment = error x KP**

Modify the program you created earlier to read encoder values:

1. Add a constant for the target of encoder ticks you want the motors to achieve; make this value about 75% of the ‘encoder ticks per sample’ value you made a note of earlier (in our case 60 × 0.75 = 45):
`TARGET = 45`
2. Add a constant (KP) for the proportional change which will be multiplied by the error to create the motor adjustment. This constant will need tuning, but a good starting point is 1 divided by the ‘encoder ticks per sample’ (e.g. 1 / 60 = 0.0166~)
`KP = 0.02`
3. At the start of the infinite loop, calculate the error for each motor by subtracting the encoder value from the target:
~~~ python
	while True:
		e1_error = TARGET - e1.value
		e2_error = TARGET - e2.value
~~~

4. Calculate the new motor speed by adding the error and multiplying it by the proportional constant:
~~~ python
    m1_speed += e1_error * KP
    m2_speed += e2_error * KP
~~~
5. The motor speed needs to be between 0 and 1, so clamp the value using max and min:
~~~ python
    m1_speed = max(min(1, m1_speed), 0)
    m2_speed = max(min(1, m2_speed), 0)
~~~

6. Update the robot’s speed to the new motor values:
~~~ python
    r.value = (m1_speed, m2_speed)
~~~

7. Add some debugging code to print the motor speed after the encoder values; this will be useful for tuning:
~~~ python
    print("e1 {} e2 {}".format(e1.value, e2.value))
    print("m1 {} m2 {}".format(m1_speed, m2_speed))
~~~

8. Before the program sleeps for the sample time, you need to reset the encoders:
~~~ python
    e1.reset()
    e2.reset()
    sleep(SAMPLETIME)
~~~
9. Run your program – you will see the motor’s speed being adjusted each time the encoders are sampled, based on the error.

View the complete proportional.py code listing at <https://github.com/martinohanlon/RobotPID>.

Proportional control should be enough to stabilise your motors’ speed and keep them turning at about the correct speed, but when there is a large error or you want the speed to adjust quickly, you will get a large overshoot and your robot will react erratically, swinging left to right – this is where derivative control helps.

