# HardwareMap

`HardwareMap` is a class that provides access to the hardware devices connected to the robot. It is used to get references to motors, servos, sensors, and other devices.

Every OpMode has a `hardwareMap` property that you can use to access the hardware devices. 
The `hardwareMap` is a map that stores the devices by their names, which are defined in the configuration file.
Creating a configuration file is discussed in the [FTC Docs](https://ftc-docs.firstinspires.org/en/latest/hardware_and_software_configuration/configuring/index.html).

Here is an example of using the `hardwareMap` to get a motor:

```java
public class ExampleOpMode extends OpMode {
    private DcMotor motor;

    @Override
    public void init() {
        motor = hardwareMap.get(DcMotor.class, "motor");
    }
}
```

We can only access the `hardwareMap` property in the `init`, `init_loop`, `start`, and `loop` methods of an OpMode,
or in the `runOpMode` method of a LinearOpMode, as these are the methods where the hardware is available.

The `get` method of the `hardwareMap` takes two parameters: the class of the device you want to get and the name of the device as defined in the configuration file.

Here are some common device classes you can use with the `get` method:
- `DcMotor` or `DcMotorEx`: for DC motors
- `Servo`: for servos
- `CRServo`: for continuous rotation servos
- `IMU`: for inertial measurement units; there is one built into the REV Expansion Hub and REV Control Hub
- `DistanceSensor`: for distance sensors

Many of these device classes are explained in more detail in the [Hardware](../hardware/overview.md) section.