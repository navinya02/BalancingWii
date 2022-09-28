# BalancingWii
Hello friends this post is about DIY self balancing robot in this post I’ll show how you can build your own Self balancing robot.  I have tried to build the project but failed not get results as expected.but this robot turn out quite good and accurate, though this is not perfect but best as compare to my previous bots.  I have use a custom made PCB, Arduno nano, MPU6050, A4988 driver, HC-05 bt module, MDF board and some hardware to build this self balancing robot,detail material list you can found further in this post.Balancingwii firmware and EZ-GUI android app is used in this project to control robot via Bluetooth connection.
This is stable 1.0 release of balancing robot (based on modified).

New features:

Fall down?! New auto rise (stand up) function! (can be activated via box in GUI). Now it's also possible to stand up manually when it's fall down.
Position hold (can be activated via box in GUI). Try to play, how it returns when you are pushing/kicking the robot.
Possibility to control/steer from Android device by MultiWii EZ-GUI tool (go to Config -> Advanced -> Model control New)
More stability and speed accordingly.
Predefined PIDs.
Simple mode for newcomers.
Set of code refactorings and cleaning.

Apps: 
https://play.google.com/store/apps/details?id=ru.shokurov.mspcontrol 
https://play.google.com/store/apps/details?id=com.ezio.multiwii

=================================== BalancingWii

Hardware:

Arduino nano (atmega328p)
mpu6050 gyro-accelerometer (GY_521)
any RC receiver with CPPM (ppmsum) output OR serial Bluetooth module like HC-05
A4988 motor drivers with 1/8 microstepping configuration (see http://www.pololu.com/product/1182/ for details)
Nema 17 stepper motors
1/8 Buggy Wheels
Buzzer
Pinout for Arduino nano (atmega328p):

A0 - V_BATPIN: after the resistor divisor we should get [0V;5V]->[0;1023] on analogue V_BATPIN with R1=33k and R2=51k, i.e. (+12v)51k(A0 pin)33k(GND)
A2 - BUZZERPIN
I2C:

A4 - SDA
A5 - SCL
RC control:

D2 - CPPM (PPM_SUM)
Motor driver pins:

D5 - STEP1 (PORTD 5)
D6 - STEP2 (PORTD 6)
D7 - DIR1 (PORTD 7)
D8 - DIR2 (PORTB 0)
D4 - ENABLE (for both)
If you look to the tail of the robot:

right motor = STEP1 & DIR1
left motor = STEP2 & DIR2
Also see for new defines added with this project for robot setup:

#define CURRENT_AXIS PITCH // possible to choose ROLL or PITCH axis as current.

//#define INVERT_CURRENT_AXIS // invert current axis sign, i.e. instead of turning sensor board

//#define REVERSE_MOTORS_DIRECTION // reverse both motors direction

#define MAX_SPEED 400 // should be <= 500 #define MAX_TARGET_ANGLE 120 // where 10 = 1 degree, should be <= 15 degree (i.e. <= 150) #define MAX_STEERING 90 // should be <= 100

//#define GY_521_INVERTED_BY_Z // Chinese 6 DOF with MPU6050, LLC, inverted/reversed by Z
