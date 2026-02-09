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
Create a function block FC “Pozycja krańcowa” (End Position). Inside this block, prepare a program responsible for operating the pneumatic cylinders.

  - Pressing the ON button (I0.1) causes Cylinder A (Q0.3) and Cylinder B (Q0.1) to extend
  - Cylinder B may extend only when Cylinder A reaches its upper position (and the ON button remains pressed)
  - If the button is released before Cylinder A reaches the upper position, Cylinder A should automatically retract

The cylinders can be retracted at any moment by pressing the OFF button (I0.0)

#8 PROGRAM: Element Position Control (FC005_Element_Position_Control [FC8])
Create a function block FC “Kontrola pozycji elementu” (Element Position Control). The inspection station consists of three presence sensors: P1 (I1.3), P2 (I1.4), and P3 (I1.5). Depending on the state of the sensor signals, activate the appropriate output indicating the inspection status:

  - When all sensors are HIGH, the detected part is correct — the lamp %Q0.4 should be continuously ON
  - When one sensor is missing (only two are HIGH), the lamp should flash at 2 Hz
  - When at most one sensor is HIGH, the lamp must remain OFF

#9 PROGRAM: Gripper Control (FC006_Robot_Gripper_Control [FC9])
Create a function block FC “Kontrola chwytaka robota” (Robot Gripper Control). Inside this block, prepare a program responsible for controlling the robot’s gripper %Q0.2. The device is operated using two physical input buttons: ON (%I0.1), OFF (%I0.0)

  - Pressing ON closes the gripper %Q0.2.
  - Pressing OFF opens the gripper %Q0.2.

The lamp %Q0.4 should turn ON when the gripper is correctly closed
