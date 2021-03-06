# Writeup

## Scenarios

### Scenario 2 - Body rate and roll/pitch control

Motor commands calculation was implemented in [/cpp/src/QuadControl::GenerateMotorCommands method ](/src/QuadControl.cpp#L56-L87)

Body rate control was implemented in [/cpp/src/QuadControl::BodyRateControl method ](/src/QuadControl.cpp#L89-L103) as P controller.

Roll/pitch control was implemented in [/cpp/src/QuadControl::RollPitchControl method ](/src/QuadControl.cpp#L116-L159) as P controller.

`kpPQR` parameter was set to `92, 95, 5`

`kpBank` parameter was set to `10`

![](./img/scenario2.png)

```
Simulation #83 (../config/2_AttitudeControl.txt)
PASS: ABS(Quad.Roll) was less than 0.025000 for at least 0.750000 seconds
PASS: ABS(Quad.Omega.X) was less than 2.500000 for at least 0.750000 seconds
```

### Scenario 3 - Position/velocity and yaw angle control

Altitude control was implemented in [/cpp/src/QuadControl::AltitudeControl method ](/src/QuadControl.cpp#L161-L201) as PD controller.

Lateral control was implemented in [/cpp/src/QuadControl::LateralPositionControl method ](/src/QuadControl.cpp#L204-L249) as PD controller.

Yaw control was implemented in [/cpp/src/QuadControl::YawControl method ](/src/QuadControl.cpp#L252-L272) as P controller.

All parameters `kpPosXY`, `kpPosZ`, `KiPosZ` was set to `30`

`kpVelXY` and `kpVelZ` parameters were set to `10`

`kpYaw` 3rd (z) component of `kpPQR` was left same as before `5`

![](./img/scenario3.png)

```
Simulation #88 (../config/3_PositionControl.txt)
PASS: ABS(Quad1.Pos.X) was less than 0.100000 for at least 1.250000 seconds
PASS: ABS(Quad2.Pos.X) was less than 0.100000 for at least 1.250000 seconds
PASS: ABS(Quad2.Yaw) was less than 0.100000 for at least 1.000000 seconds
```

### Scenario 4 - Non-idealities and robustness

As red quad didn't end up in target testination, I added integral control to altitude controller (PID controller now) and increased `KiPosZ` parameter to `40`.

Green seems to use a trajectory that goes to the left a little bit and red seems to take time to settle because of mass.

![](./img/scenario4.png)

```
Simulation #91 (../config/4_Nonidealities.txt)
PASS: ABS(Quad1.PosFollowErr) was less than 0.100000 for at least 1.500000 seconds
PASS: ABS(Quad2.PosFollowErr) was less than 0.100000 for at least 1.500000 seconds
PASS: ABS(Quad3.PosFollowErr) was less than 0.100000 for at least 1.500000 seconds
```

### Scenario 5  - Trajectory follow

Quad following trajectory `FigureEight` seems to be doing it quite well. Quad following trajectory `FigureEightFF.txt` is struggling and flying a little bit off.

![](./img/scenario5.png)

```
Simulation #94 (../config/5_TrajectoryFollow.txt)
PASS: ABS(Quad2.PosFollowErr) was less than 0.250000 for at least 3.000000 seconds
```

### Scenario X - Test many quads

In this scenario quads seems to fly to very different directions at first, but once they settle they seems to follow path quite well.

![](./img/scenario6.png)
