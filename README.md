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
| 0           | 1           | Turn right                  | TURN_RIGHT / STOP_TURNING |
| 1           | 0           | Turn left                   | TURN_LEFT / STOP_TURNING  |
| 1(<1 sec)   | 1(<1 sec)   | Start driving forward/Stop  | FORWARD_STOP              |
| 1 (> 1 sec) | 1 (> 1 sec) | Initiate autonomous driving | AUTONOMOUS                |
