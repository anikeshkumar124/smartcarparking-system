# smartcarparking-system
Explanation:
Include Libraries:
Servo.h: This library is used for controlling the servo motor.
Wire.h: Used for I2C communication with the LCD.
LiquidCrystal_I2C.h: This library simplifies controlling the 20×4 LCD screen using I2C communication.
Servo Motor and IR Sensor Definitions:
The code defines pins for the servo motor and IR sensors. For example, ir_enter is defined as pin 2 for the entrance sensor, and ir_back is defined as pin 4 for the back sensor.
IR Sensor Variables:
The state of each parking place is stored in the variables S1, S2, S3, S4, S5, and S6 (1 or 0).
When an automobile is arriving or leaving, the variables flag1 and flag2 are utilized as flags to monitor this information.
slot variable keeps track of the number of available parking slots.
Setup Function:
The setup() function initializes the serial communication, pin modes for IR sensors, and the servo motor.
It initializes the LCD and displays a welcome message for 2 seconds.
Read_Sensor() function is called to read the initial status of parking slots and calculate the number of available slots.
Loop Function:
The loop() function continuously runs the main logic of the system.
It calls Read_Sensor() to update the status of parking slots.
It displays the number of available slots and the status of each slot on the LCD.
It checks the status of entrance and back IR sensors to determine if a car is entering or exiting.
When a car enters, it checks if there are available slots and opens the barrier (servo motor) while decrementing the available slot count. If parking is full, it displays a “Parking Full” message.
When a car exits, it opens the barrier and increments the available slot count.
After a delay, the barrier is closed, and the flags are reset.
Read_Sensor Funct
The Read_Sensor() function is used to read the status of the IR sensors for all parking slots and update the corresponding variables S1 to S6. The sensor values are stored in variables S1 through S6, each of which is associated with a particular parking spot. The code checks the condition of each infrared sensor (ir_car1 through ir_car6) using the digitalRead function. The associated S variable is set to 1, indicating that the relevant parking spot is occupied, if the sensor detects the presence of an automobile (returns a logic low or 0). It is noteworthy that the code given initializes all S variables to 0 before to reading the sensors, so guaranteeing a fresh start for every sensor reading loop.
