## PID Controller

A PID controller continuously calculates an error and applies a corrective action to resolve the error; in this case, the error is the motor spinning at the wrong speed and the corrective action is changing the power to the motor. It is this continuous testing of the motor’s speed and adjusting it to the correct speed which will make your robot’s motors spin at the correct speed and go straight. 

PID is a ‘control loop feedback’ mechanism

The controller will have a target motor speed that it wishes to maintain; each time the encoder values are sampled, it will calculate the difference (or error) between the target speed and the actual speed and apply an adjustment to the motor speed. If the adjustment overshoots the next time the encoders are sampled, a smaller opposite adjustment will be made. Over time, the adjustments will even out and the motors will run at a constant speed (or at least that’s the theory!).

You will be changing the program you created to read encoder values to calculate an error and apply an adjustment using proportional, derivative, and integral control.
