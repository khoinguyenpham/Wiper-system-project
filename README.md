# Wiper system project
We will try to use different methods for the same project to see how we can use different subsystems and different blocks to generate or to model the same software component. The main target for this software component is the duty cycle for the motor, the wiper motor.

## Model

![image](https://github.com/user-attachments/assets/4acde372-8e52-48cb-82f0-9b84715e8216)

### Wiper system control inputs

Input 1: WiprMode -> wiper modes of operations, including off mode - Off(0), low speed - LoSpd(2), high speed(3) - HiSpd, and automative mode - Aut(1).

Input 2: RainSnsrErr -> rain sensor error, there is a rain sensor error or not for the rain values, including normal, no error(0), and error(1).

Input 3: WiprSpdReq -> wiper speed request, this is will be used in the automatic mode that what mode exactly you want in the automatic mode and in the scheduler. Require speed level in case of automatic mode [0 1 2 3 4 5 6 7].

Output 1: the output of this software component will be the wiper motor, be the duty cycle.

Output 2: a flag that represents if the driver is active or not.

f(x): This functionality is executed every ten millisecond. So from this information I will configure the model or the this software component to run at 10 milliseconds.


