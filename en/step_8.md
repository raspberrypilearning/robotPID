## Tune the system
To get PID control working for your setup, it will need to be tuned; this will involve modifying the constants KP, KD, and KI. There is no exact science to this and there will be a certain amount of trial, error, and intuition required before you find the right setup for your robot.

The following tips however should improve your tuning:
1. Start by modifying the KP constant and get the performance as good as you can before moving onto KD and then finally KI.
2. If the motor adjustments are too aggressive, swinging between too fast and too slow, reduce the constant.
3. If the motor speed isn’t changing fast enough, increase the constant.
4. Make any change in small increments; even a very small change can have a dramatic effect.

Once tuned, each motor should settle down to a speed which is close to the encoder target.