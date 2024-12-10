# OpModes

OpModes are the robot programs that run on the robot controller. 
They are written in Java and are run on the robot controller (either a REV Control Hub or Android phone plugged into a REV Expansion Hub).
The robot controller phone is connected to the robot's control system and runs the robot's programs. 
The robot controller phone is connected to the driver station (either a REV Driver Hub or Android phone) via Wi-Fi.

There are two types of OpMode annotations: Autonomous and TeleOp,
which correspond to the two modes of operation in a FIRST Tech Challenge match.

There are also two types of OpMode classes: LinearOpMode and OpMode.
Both types of OpMode classes require the `@Autonomous` or `@TeleOp` annotation 
to tell the robot controller which type of OpMode it is,
allowing you to select the OpMode from the driver station.

## OpMode Properties

Both types of OpModes have the following properties:
- `hardwareMap`: a map of hardware devices (e.g., motors, servos, sensors) that are connected to the robot controller. 
This will be discussed in more detail in a later section.
- `telemetry`: a way to send information back to the driver station.
- `gamepad1` and `gamepad2`: the two gamepads connected to the driver station.

```admonish important
You can only access these properties in overriden methods:
- `runOpMode` for LinearOpMode
- `init`, `init_loop`, `start`, and `loop` for OpMode
```

### Telemetry

The `telemetry` property is used to send information back to the driver station,
which is essentially the console for the robot controller.

You can use the `telemetry` property to send messages, display values, and log data.
This is useful for debugging and monitoring the robot's behavior during a match.

There are three main methods you can use with the `telemetry` property:
- `addData(String caption, Object value)`: adds a piece of data to the telemetry.
- `addLine(String line)`: adds a line of text to the telemetry.
- `update()`: updates the telemetry and sends the data to the driver station.

Unlike the console, the telemetry is not real-time, so you need to call the `update` method to send the data to the driver station.

### Gamepads

The `gamepad1` and `gamepad2` properties represent the two gamepads connected to the driver station.

Each gamepad has the following properties:
- `left_stick_x`, `left_stick_y`, `right_stick_x`, `right_stick_y`: the x and y values of the left and right joysticks.
- `left_trigger`, `right_trigger`: the values of the left and right triggers.
- `a`, `b`, `x`, `y`: the state of the A, B, X, and Y buttons.
- `dpad_up`, `dpad_down`, `dpad_left`, `dpad_right`: the state of the directional pad buttons.
- `left_bumper`, `right_bumper`: the state of the left and right bumpers.

The buttons also have PlayStation-style aliases:
- `triangle` for `y`
- `circle` for `b`
- `cross` for `a`
- `square` for `x`

The `a`, `b`, `x`, `y`, `dpad_up`, `dpad_down`, `dpad_left`, `dpad_right`, `left_bumper`, and `right_bumper` properties 
are `boolean` values that are `true` if the button is pressed and `false` if it is not.

The `left_stick_x`, `left_stick_y`, `right_stick_x`, and `right_stick_y`, properties
are `double` values that range from `-1.0` to `1.0`, where `-1.0` is full left or up, `1.0` is full right or down, and `0.0` is centered.

The `left_trigger` and `right_trigger` properties 
are `double` values that range from `0.0` to `1.0`, where `0.0` is not pressed and `1.0` is fully pressed.

The gamepad properties are updated automatically every time the `loop` method is called.
In a `LinearOpMode`, the gamepad properties are updated automatically every iteration of the `while (opModeIsActive())` loop.

## LinearOpMode

LinearOpMode is a class that extends the `OpMode` class and provides a linear structure for writing OpModes.
This means that the code in a LinearOpMode runs sequentially from the start of the `runOpMode` method to the end.

It only has one method: `runOpMode`, which is called when the OpMode is selected from the driver station.

Here is an example of a LinearOpMode:

```java
@Autonomous 
public class ExampleOpMode extends LinearOpMode {
    @Override
    public void runOpMode() {
        //information about motors and other hardware is in a later section
        DcMotor motor = hardwareMap.get(DcMotor.class, "motor");
        
        //code to run before the start of the match
        waitForStart();
        
        motor.setPower(1.0);
        telemetry.addData("Motor Position", motor.getCurrentPosition());
        telemetry.update();
    }
}
```

Everything that the robot does during the match is written inside the `runOpMode` method.
The `waitForStart` method is called to wait for the user to press the "Start" button on the driver station.

## OpMode

`OpMode` is a class that provides a more flexible structure for writing OpModes.
It was the original class used for writing OpModes in the FIRST Tech Challenge,
but LinearOpMode has also become popular due to its simplicity.

The `OpMode` class has four methods that you can override:
- `init`: called when the OpMode is initialized.
- `init_loop`: called repeatedly while the OpMode is waiting for the user to press the "Start" button,
but after the `init` method has been called.
- `start`: called when the OpMode is started.
- `loop`: called repeatedly while the OpMode is running, but after the `start` method has been called.

Here is an example of an OpMode:

```java
@TeleOp
public class ExampleOpMode extends OpMode {
    DcMotor motor;
    
    @Override
    public void init() {
        motor = hardwareMap.get(DcMotor.class, "motor");
    }

    @Override
    public void loop() {
        motor.setPower(gamepad1.left_stick_y);
        telemetry.addData("Motor Power", motor.getPower());
        telemetry.update();
    }
}
```

Only the `init` and `loop` methods are required, but you can also override the `init_loop` and `start` methods if needed.

## What Type of OpMode Should I Use?

The choice between LinearOpMode and OpMode depends on the complexity of your robot program.

Personally, I mostly use `OpMode` because it provides more flexibility and control over the OpMode's behavior,
but `LinearOpMode` is easier to understand and use for beginners.