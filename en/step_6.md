## Derivative Control

Derivative control looks at how quickly or slowly the error is changing, creating a larger error if it’s changing quickly and a smaller one if slowly. This will help to smooth out the rate of change and prevent erratic changes in speed.

This is achieved by taking the previous error into account when calculating the adjustment and again multiplying by a constant (KD): 

**adjustment = (error × KP) + (previous_error × KD)**

Modify the program to implement derivative control…

1. Create a new constant (KD) for the derivative control. Again, this value will need to be changed to get the best results for your setup; a good starting value is half the value of KP:
`KD = 0.01`

2. Create two variables to hold the previous errors and set them to 0:
~~~ python
	e1_prev_error = 0
	e2_prev_error = 0
~~~

3. Modify the code which calculate the speeds for motor 1 and 2 to taken into account the previous error:
~~~ python
    m1_speed += (e1_error * KP) + (e1_prev_error * KD)
    m2_speed += (e2_error * KP) + (e1_prev_error * KD)
~~~

4. At the end of the loop, set the previous error variables to be that of the current error:
~~~ python
    sleep(SAMPLETIME)
    e1_prev_error = e1_error
    e2_prev_error = e2_error
~~~
	
5. Run your program. Again you will see the motor speed change in relation to error and over time, it should stabilise to a more consistent speed.
Proportional and derivative (PD) control should provide a good level of performance but may not provide consistency of speed over time – integral control can help to bring this stability.

