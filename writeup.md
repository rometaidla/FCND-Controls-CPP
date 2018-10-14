# Writeup

## Scenarios

### Scenario 2 - Body rate and roll/pitch control

![](./img/scenario2.png)

```
Simulation #83 (../config/2_AttitudeControl.txt)
PASS: ABS(Quad.Roll) was less than 0.025000 for at least 0.750000 seconds
PASS: ABS(Quad.Omega.X) was less than 2.500000 for at least 0.750000 seconds
```

### Scenario 3 - Position/velocity and yaw angle control

![](./img/scenario3.png)

```
Simulation #88 (../config/3_PositionControl.txt)
PASS: ABS(Quad1.Pos.X) was less than 0.100000 for at least 1.250000 seconds
PASS: ABS(Quad2.Pos.X) was less than 0.100000 for at least 1.250000 seconds
PASS: ABS(Quad2.Yaw) was less than 0.100000 for at least 1.000000 seconds
```

### Scenario 4 - Non-idealities and robustness

![](./img/scenario4.png)

```
Simulation #91 (../config/4_Nonidealities.txt)
PASS: ABS(Quad1.PosFollowErr) was less than 0.100000 for at least 1.500000 seconds
PASS: ABS(Quad2.PosFollowErr) was less than 0.100000 for at least 1.500000 seconds
PASS: ABS(Quad3.PosFollowErr) was less than 0.100000 for at least 1.500000 seconds
```

## Rubrics criterias

### Implemented body rate control in C++.

Body rate control is implemented in [/cpp/src/QuadControl::BodyRateControl method ](/src/QuadControl.cpp#L89-L103) as P controller.

### Implemented roll pitch control in C++.

Roll/pitch control is implemented in [/cpp/src/QuadControl::RollPitchControl method ](/src/QuadControl.cpp#L116-L159) as P controller.

### Implemented altitude controller in C++.

Altitude control is implemented in [/cpp/src/QuadControl::AltitudeControl method ](/src/QuadControl.cpp#L161-L201) as PID controller.

### Implemented lateral position control in C++.

Lateral control is implemented in [/cpp/src/QuadControl::LateralPositionControl method ](/src/QuadControl.cpp#L204-L249) as PD controller.

### Implemented yaw control in C++.

Yaw control is implemented in [/cpp/src/QuadControl::YawControl method ](/src/QuadControl.cpp#L252-L272) as P controller.

### Implement calculating the motor commands given commanded thrust and moments in C++.

Motor command are calculated in [/cpp/src/QuadControl::GenerateMotorCommands method ](/src/QuadControl.cpp#L56-L87)
