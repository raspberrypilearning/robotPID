## Integral
Integral control helps to deliver steady state performance by adjusting for slowly changing errors. It does this by keeping a sum of all the previous errors and applying a constant (KI) to the adjustment:

*adjustment = (error × KP) + (previous_error × KD) + (sum_of_errors × KI)*

Modify the program to implement integral control:

1. Create a constant for the integral control (KI); a good starting point is half the value of KD:
`KI = 0.005`

2. Create two variables to hold the sum of all previous errors and set them to 0:
~~~ python
	e1_sum_error = 0
	e2_sum_error = 0
~~~

3. Modify the speed calculation to take into account the sum:
~~~ python
    m1_speed += (e1_error * KP) + (e1_prev_error * KD) + (e1_sum_error * KI)
    m2_speed += (e2_error * KP) + (e1_prev_error * KD) + (e2_sum_error * KI)
~~~

4. At the end of the loop, increment the sum variables by the current error value:
~~~ python
    sleep(SAMPLETIME)
    e1_sum_error += e1_error
    e2_sum_error += e2_error
~~~

5. Run the program. You should see over time that the motor speeds start to stabilise.
