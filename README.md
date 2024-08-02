# WIPER SYSTEM PROJECT
I will try to use different methods for the same project to see how I can use different subsystems and different blocks to generate or to model the same software component. The main target for this software component is the duty cycle for the motor, the wiper motor.

## Model in root level

<img width="443" alt="image" src="https://github.com/user-attachments/assets/dad30621-4aea-45cc-87ca-b9c5f57f7c90">

### Wiper system control inputs/outputs

Input 1: WiprMode -> wiper modes of operations, including off mode - Off(0), low speed - LoSpd(2), high speed(3) - HiSpd, and automative mode - Aut(1).

Input 2: RainSnsrErr -> rain sensor error, there is a rain sensor error or not for the rain values, including normal, no error(0), and error(1).

Input 3: WiprSpdReq -> wiper speed request, this is will be used in the automatic mode that what mode exactly you want in the automatic mode and in the scheduler. Require speed level in case of automatic mode [0 1 2 3 4 5 6 7].

Output 1: WiprMotPwmDutyCyc -> PWM command to the wiper control, the output will be the wiper motor, be the duty cycle.

Output 2: WiprActv -> a flag that represents if the wiper motor is active or not, including not active(0), and active(1).

f(x): This functionality is executed every ten millisecond. So from this information I will configure the model or the this software component to run at 10 milliseconds.

### Wiper system control processing

WinprMode 
- 0: Off: WiprMotPwmDutyCyc = 0%

- 1: Aut: + if RainSnsrErr is TRUE -> PWM shall 0
          
          + WiprSpdReq require speed level in case of automatic mode 0-7.
                    
          + Rain sensor to PWM table: 0 40% 45% 50% 55% 60% 65% 70%.
                    
          + Require have a smooth PWM command in automatic mode -> avoid abrupt changes.
                    
- 2: LoSpd: WiprMotPwmDutyCyc = 40%
          
- 3: HiSpd: WiprMotPwmDutyCyc = 70%
