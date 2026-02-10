This folder contains all exercises and project files created during the Siemens TIA Portal – Level 1 training.
The goal of this section is to provide a clear structure for each task, along with translated instructions and clean project files that can be easily opened, reviewed, or reused.

The list below includes all exercises. After each task name, a pair of parentheses will contain the exact TIA Portal function/block name where the solution is implemented

#1 PROGRAM: Closing Gripper #1 (FC001_Close_Gripper [FC1])
In the block Main [OB1], write the first program that will control the gripper. Pressing the green ON button %I0.1 should activate the gripper closing output %Q0.2

#2 PROGRAM: Operation of Pusher A (FC002_PusherA_Operation [FC2])
In a new network inside Main [OB1], write a program that controls Cylinder A located in the workstation.

  - Pressing the green ON button (%I0.1) should extend Cylinder A (%Q0.3)
  - Pressing the red OFF button (%I0.0) should retract Cylinder A (%Q0.0

#3 PROGRAM: Operation of Pusher B (FC003_PusherB_Operation [FC3])
In a new network inside Main [OB1], write a program responsible for controlling the second actuator — Cylinder B.

  - To extend Cylinder B (%Q0.1), press the silver switch (%I1.3)
  - To retract Cylinder B (%Q0.5), press the silver switch (%I1.4)

#4 PROGRAM: Closing Gripper #2 (FC001_Close_Gripper#2 [FC4])
Introduce additional operating conditions for the gripper. The gripper %Q0.2 may be closed only when:

  - Cylinder A is in the upper position (%I0.6)
  - Cylinder B is in the upper position (%I0.4)
  - The green ON button %I0.1 is pressed

#5 PROGRAM: Operation of the Pusher – Safety Functions (FC002_PusherA_Operation_Safty [FC5])
In the existing program, introduce safety conditions using feedback signals from the sensors.

  - Pressing the ON button (%I0.1) should extend Cylinder A (%Q0.3), but the output must be turned off as soon as the upper position sensor (%I0.6) is activated
  - Pressing the OFF button (%I0.0) should retract Cylinder A (%Q0.0), but the output must be turned off when the lower position sensor (%I0.3) is activated.

Additionally: Program the emergency stop switch. When the emergency stop button (%I0.2) is pressed, it must prevent any movement of all devices

#6 PROGRAM: Pusher Operation Signaling (FC002_PusherA_Operation_Signalling [FC6])
Introduce a modification to the pusher operation signaling program.

  - During the movement of Cylinder A (either upward or downward), the lamp %Q0.4 should flash at a frequency of 10 Hz.
Additionally: when the cylinder is in an end position (lower or upper) the lamp should flash at a frequency 1Hz

#7 PROGRAM: End Position (FC004_EndPosition [FC7])
Create a function block FC. Inside this block, prepare a program responsible for operating the pneumatic cylinders.

  - Pressing the ON button (I0.1) causes Cylinder A (Q0.3) and Cylinder B (Q0.1) to extend
  - Cylinder B may extend only when Cylinder A reaches its upper position (and the ON button remains pressed)
  - If the button is released before Cylinder A reaches the upper position, Cylinder A should automatically retract

The cylinders can be retracted at any moment by pressing the OFF button (I0.0)

#8 PROGRAM: Element Position Control (FC005_Element_Position_Control [FC8])
Create a function block FC. The inspection station consists of three presence sensors: P1 (I1.3), P2 (I1.4), and P3 (I1.5). Depending on the state of the sensor signals, activate the appropriate output indicating the inspection status:

  - When all sensors are HIGH, the detected part is correct — the lamp %Q0.4 should be continuously ON
  - When one sensor is missing (only two are HIGH), the lamp should flash at 2 Hz
  - When at most one sensor is HIGH, the lamp must remain OFF

#9 PROGRAM: Gripper Control (FC006_Robot_Gripper_Control [FC9])
Create a function block FC. Inside this block, prepare a program responsible for controlling the robot’s gripper %Q0.2. The device is operated using two physical input buttons: ON (%I0.1), OFF (%I0.0)

  - Pressing ON closes the gripper %Q0.2.
  - Pressing OFF opens the gripper %Q0.2.

The lamp %Q0.4 should turn ON when the gripper is correctly closed

#10 PROGRAM: Modification – Robot Gripper Control (FC006_Robot_Gripper_Control#2 [FC10])
Modify the program in the block FC Robot Gripper Control. Use an appropriate SR/RS latch (set–reset flip‑flop) block to control the state of the gripper

#11 PROGRAM: Pneumatic Lift (FC007_Pneumatic_Lift [FC11])
Create a function block FC “Pneumatic Lift”. Pressing the switch I1.3 initiates the extension of Cylinder A (Q0.3). The cylinder must stop when the upper position sensor (I0.6) becomes active. Similarly, in the opposite direction, the signal I1.4 starts the retraction of Cylinder A (Q0.0), and the stopping condition is the lower position sensor (I0.3) going HIGH

#12 PROGRAM: Alarm Handling (FC008_Alarms_Handling [FC12])
Create a function block FC “Alarm Handling”.
Inside this block, implement a mechanism for handling alarm conditions. The following signals must be monitored:

| Signal Name        | Address | Normal Operating State  |
|--------------------|---------|-------------------------|
| Fuse               | %I1.0   | 1                       |
| Motor Temperature  | %I1.1   | 1                       |
| Pusher Interlock   | %I1.2   | 0                       |
| Pressure OK        | %I1.3   | 0                       |

The alarm is reset using the button %I1.5. The lamp %Q0.4 indicates the system state:

When the alarm and its cause are active, the lamp should flash at 5 Hz. When the alarm is active but the cause has cleared, the lamp should flash at 1 Hz (indicating readiness for operator reset). When no alarm is present, the lamp should remain continuously ON

#13 PROGRAM: Automatic Cycle (FC009_Auto_Cycle [FC13])
Create a function block FC “Automatic Cycle”. This block is responsible for controlling the cylinders and the gripper. The sequence of the cycle is as follows:

STAGE 1 — Single Cycle
Step 1: Pressing the green button (%I0.1) closes the gripper (%Q0.2).
Step 2: A closed gripper (%I0.5) triggers the extension of Cylinder A (%Q0.3).
Step 3: Reaching the upper position of Cylinder A (%I0.6) triggers the extension of Cylinder B (%Q0.1).
Step 4: When both cylinders are extended, open the gripper (%Q0.2).
Step 5: Opening the gripper (%I0.5) triggers the retraction of Cylinder B (%Q0.5).
Step 6: Reaching the lower position of Cylinder B (%I0.7) triggers the retraction of Cylinder A (%Q0.0).

STAGE 2 — Automatic Operation
Automate the cycle: After pressing the green button (%I0.1), the program should continuously repeat steps 1–6 in a loop. Pressing the red button (%I0.0) must allow the system to finish the current cycle and then stop automatic operation.

#14 PROGRAM: One Button – One Lamp (FC010_OneButton_OneLight [FC14])
Create a function block FC “One Button – One Lamp”. The program should operate as follows:

If the lamp %Q0.4 is OFF, pressing the Start button (%I0.1) should turn it ON
If the lamp %Q0.4 is ON, pressing the Start button (%I0.1) should turn it OFF

#15 PROGRAM: Voltage Control (FC011_Voltage_Control [FC15])
Create a function block FC “Voltage Control”. The analog output range displayed on QW80 is from 0 V to 10 V. To control the analog output voltage, you must generate an INT value in the range 0 to 27648 (where 27648 is the scaling constant). Relationship between PLC value and output voltage:

INT = 0 → 0 V
INT = 27648 → 10 V

Depending on the state of inputs I1.0 and I1.1, generate the appropriate output voltage:

I1.0 = TRUE or I1.1 = TRUE → QW80 = 5 V
I1.0 = TRUE and I1.1 = TRUE → QW80 = 10 V
No active input → QW80 = 0 V

#16 PROGRAM: Calculations (FC012_Calculations [FC16])
Create a function block FC "Calculations".
Write a program that performs the following operations:

Production status from two production lines:
Status = Sum1 + Sum2 - Losses

Increase the parameter Sum by the value of parameter ParAdd each time the operator presses the green button:
Sum = Sum + ParAdd

Ensure that the value of ParAdd is within the range from 1 to 4

#17 PROGRAM: Labeling Machine Handling (FC013_Labeler_Control [FC17])
Create a function block FC "Labeling Machine Handling". When a new roll is installed, the operator loads its length using the parameter Dl_Roll (the roll length is given in millimeters, for example 5000 mm).
Each time the operator presses the button I0.1, the stepper motor advances the roll by the length defined in the parameter Dl_Label (given in millimeters, for example 200 mm for a PET bottle label).
The operator replaces the roll and confirms the replacement using the button I1.0. Prepare a program that: monitors the number of bottles with a label applied (piece counter), monitors the roll state (number of labels remaining on the active roll), stores the number of used rolls (roll counter), and implements appropriate protections (for example: prevention of negative roll values).
Additionally: the lamp %Q0.4 should flash when the roll is close to the end (less than 3 labels remaining)

#18 PROGRAM: Buffer Filling (FC014_Buffer_Filling [FC18])
Create a function block FC "Buffer Filling". The sensor I1.3 returns a HIGH state when a new bottle enters the buffer. The exit of a bottle from the buffer is signaled by a HIGH state on input I1.5. The lamp %Q0.4 indicates the buffer status:

  - Lamp OFF when the buffer is empty
  - Lamp flashes at 1 Hz when the number of bottles in storage is greater than 0 and less than 7
  - Lamp flashes at 5 Hz when the buffer is almost full (7–9 bottles)
  - Lamp is continuously ON when the buffer is full (10 bottles)

Use an appropriate counter and comparators. Use input %I0.0 to reset the counter. Additionally: prevent the counter value from increasing when the buffer is already full

#19 PROGRAM: Lift Sequence (FC015_Lift_Sequence [FC19])
Create a function block FC "Lift Sequence". Pressing the ON button %I0.1 advances the system to the next step of the sequence, implemented through a counter mechanism. Depending on the current program number, execute the appropriate sequence operation.


| Program Number | Operation                               |
|----------------|-----------------------------------------|
| 1              | Closing the gripper %Q0.2               |
| 2              | Extending Cylinder A %Q0.3              |
| 3              | Extending Cylinder B %Q0.1              |
| 4              | Opening the gripper %Q0.2               |
| 5–7            | Lamp flashing at 2 Hz                   |
| 8–10           | Retracting Cylinder B %Q0.5             |
| 11             | Retracting Cylinder A %Q0.0             |
| 12             | Lamp flashing at 2 Hz                   |
| 13             | End of sequence – counter reset         |

#20 PROGRAM: Pulse Generator (FC016_Pulse_Generator [FC20])
Create a function block FC "Pulse Generator". Pressing the ON button %I0.1 starts the operation of the pulse generator. Pressing the OFF button %I0.0 deactivates the pulse generator. The generator output should be indicated by the lamp %Q0.4. Additionally: The ON time (T_ON) and OFF time (T_OFF) parameters should be set using variables stored in a data block (DB).

#21 PROGRAM: Motor with Cooling (FC017_Motor_With_Cooling [FC21])
Create a function block FC "Motor with Cooling". The program consists of several stages:

PHASE 1 – Motor Control
Starting the motor %Q0.4 is performed by pressing the green button %I0.1 for at least two seconds. This is required as protection against accidental activation. The motor can be stopped using the red button %I0.0.

PHASE 2 – Fan Control
The cooling fan is connected to output %Q0.2. The fan starts at the same moment as the motor, but it should turn off six seconds after the motor is stopped.

PHASE 3 – Emergency Stop
Program the emergency stop switch. Pressing the E‑STOP button %I0.2 must immediately stop both the motor and the fan and generate an alarm. The alarm must be reset using the Reset input %I1.5.

#22 PROGRAM: Cylinder Timeout (FC018_Cylinder_Timeout [FC22])
Create a function block FC "Cylinder Timeout". Pressing the green button I0.1 should start the upward movement of Cylinder A (toward its upper sensor). Pressing the red button I0.0 should start the downward movement of Cylinder A (toward its lower sensor). If the movement in either direction exceeds 2 seconds, an alarm must be activated and the movement must stop. While the alarm is active, the lamp should flash at a frequency of 1 Hz.
Before the program can operate again, the alarm must be reset using the button I1.5.

#23 PROGRAM: End Position – Part II (FC004_EndPosition#2 [FC23])
Modify the function block FC "End Position". Reaching the upper positions of both cylinders should cause the gripper to close. When both cylinders return to their lower positions, the gripper should open automatically.
Additionally, the operator may close the gripper at any moment using the button I1.0. However, if the cylinders return to their lower positions, opening the gripper can also be done manually using the button I1.1.
Add protection to ensure that the gripper can only be opened when both cylinders are in their lower positions.

#24 PROGRAM: Manual Sequence (FC019_Manual_Sequence [FC24])
Create a new function block FC "Manual Sequence".Write the following program:

  - Pressing button I1.0 extends Cylinder A and turns on the lamp.
  - Pressing button I1.1 extends Cylinder B and closes the gripper.
  - Pressing button I1.2 opens the gripper and turns off the lamp.
  - Pressing button I1.3 retracts the cylinders.

Additionally, ensure that the next step can only begin after the previous step has been correctly completed (verified by the appropriate sensor states).

#25 PROGRAM: Three Production Lines (FC020_Three_Production_Lines [FC25])
Create a new function block FC "Three Production Lines". The plant has three production lines, each manufacturing different automotive components. Line 1 produces 5 parts per second, line 2 produces 10 parts per second, and line 3 produces 1 part per second. The profit per part is as follows: 4 for line 1, 3 for line 2, and 39 for line 3.
Write a program that stores the number of parts produced by each production line and calculates the total profit of the plant.

Production reset (clearing part counts and profit) is activated using the red button I0.0.

#26 PROGRAM: Packaging Control (FC021_Packaging_Control [FC26])
Create a new function block FC "Packaging Control". Every 1 second a new bottle exits the production line. The bottles are packed by a robot into a carton that holds 24 units (6 rows × 4 bottles).
Write a program that stores:

  - the current number of bottles inside the carton,
  - the current row number being filled,
  - the total number of fully packed cartons

