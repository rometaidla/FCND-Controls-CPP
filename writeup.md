# Writeup

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
