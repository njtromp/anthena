# Athena
Embedded Software and Systems Lego Mindstorms EV3 Robot

## Controls

The controls library can connect to the left and right touch sensors. These should be connected to the following ports respectively:

```
ltSensor
rtSensor
```

The library emits the following events:

| Left        | Right       | Action                      | Event                     |
|-------------|-------------|-----------------------------|---------------------------|
| 0           | 0           | No change                   | -                         |
| 0           | 1           | Turn right                  | RHOLD / RELEASE / BUTTON_ACTIVITY
| 1           | 0           | Turn left                   | LHOLD / RELEASE / BUTTON_ACTIVITY |
| 1(<1 sec)   | 1(<1 sec)   | Start driving forward/Stop  | SHORT_PRESS / BUTTON_ACTIVITY             |
| 1 (> 1 sec) | 1 (> 1 sec) | Initiate autonomous driving | LONG_PRESS / BUTTON_ACTIVITY               |


## Flag 

This library is for raising and lowering the flag. With event RAISE_FLAG starts raising the flag until encoder hits >=90 and will stop the raising. With the event LOWER_FLAG starts lowering the flag until the encoder hits <=0.

 Action                      | Event                     |
-----------------------------|---------------------------|
 Raising the flag            | RAISE_FLAG                |  
 Lowering the flag           | LOWER_FLAG                | 


## DistanceSensor

The distance sensor library needs to be connected to a ultrasonic sensor.

The library emits the following events:

| Action                      | Event              |
|-----------------------------|--------------------|
| Distance < 255 cm           | APPROACHING_BEAST  |
| Distance < 12 cm            | FOUND_BEAST        |
| Distance < 10 cm            | TOO_CLOSE_TO_BEAST |

## DriveStraight

This library constantly corrects the spinning speed of the motors in order to keep it running in a straight line.

| Input         | Description                      |
|---------------|----------------------------------|
| maxPower      | The maximum power to use.        |
| leftRotation  | The encoder for the left wheel.  |
| rightRotation | The encoder for the right wheel. |

| Output        | Description                           |
|---------------|---------------------------------------|
| leftMotor     | To power setting for the left motor.  |
| rightMotor    | To power setting for the right motor. |

## HomeDetector

This library detects if the robot found the green safe zone, aka home. It assumes the safe zone is reached when the set value is detected for a certain time.
Internal there are three settings that influence the behavior of the detector.

| Input      | Description                      |
|------------|----------------------------------|
| color      | The reflective color value.      |

| Event      | Description                              |
|------------|------------------------------------------|
| GREEN      | Set to true when safe zone is detected.  |

| Setting     | Description                                                                               |
|-------------|-------------------------------------------------------------------------------------------|
| HOME_COLOR  | The value which is considdered the safe zone has.                                         |
| THRESH_HOLD | The threshold which determines the range of the color that is detected as the home color. |
| DELAY       | The time (in milliseconds) the color value is within the threshold.                       |
