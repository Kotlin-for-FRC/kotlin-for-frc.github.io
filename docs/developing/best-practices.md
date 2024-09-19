# Best Practices

This document outlines some best-practice idioms for writing Kotlin code for the FRC robot project.
More idioms can be found in the [Kotlin idioms](https://kotlinlang.org/docs/idioms.html) documentation.

## Using the `apply` function for configuration

The `apply` function is a powerful tool for configuring objects in Kotlin. It allows you to configure an object in a
block of code without having to call the setter methods. This can make your code more concise and easier to read.

Here's an example of how you can use the `apply` function to configure a `TalonFXConfiguration` instance:

```kotlin
val talon = TalonFX(1, "canivore")
val config = TalonFXConfiguration().apply {
    Slot0.kS = 1
    Slot0.kV = 1
    Slot0.kA = 1
    Slot0.kP = 1
}

init {
    talon.apply(config)
}
```

> **_NOTE:_**  `talon.apply` is calling the CTRE defined `apply` method, not the Kotlin `apply` function.

or a `SparkMax` motor controller:

```kotlin
val motor = CANSparkMax(1, CANSparkLowLevel.MotorType.kBrushless).apply {
    idleMode = IdleMode.kCoast
    inverted = true
    encoder.apply {
        inverted = false
        positionConversionFactor = 360.0
    }
}
```

The `apply` blocks can be nested to configure nested objects, like the `encoder` in the `SparkMax` example.

## Single expression functions

In Kotlin, you can define functions that consist of a single expression without using the `return` keyword. This can
make your code more concise and easier to read. The Command-based framework can utlize this feature to make command
factories more concise:

```kotlin
/* Returns a command that runs the motor forward */
fun runMotorForward() = run { motor.set(1) }

/* Returns a command that runs the motor backward */
fun runMotorBackward() = run { motor.set(-1) }

/* Returns a command that stops the motor */
fun stopMotor() = run { motor.set(0) }
```

Single-expression functions have a return type that is inferred from the expression, so you don't need to specify the
return type explicitly. The return type of these functions is `Command` because the `run` function returns a `Command`
object.

More on single-expression functions can be
found [here](https://kotlinlang.org/docs/functions.html#single-expression-functions).

## Data classes

`data class`es are equivalent to `record` classes in Java. They are used to store data and provide a `toString`,
`equals`, and `hashCode` implementation automatically. This can make your code more concise and easier to read.

```kotlin
data class ClosedLoopGains(val kP: Double, val kI: Double, val kD: Double)
```

You can create an instance of a `data class` like this:

```kotlin
val gains = ClosedLoopGains(kP = 0.1, kI = 0.01, kD = 0.001)
println(gains) // Output: "ClosedLoopGains(kP=0.1, kI=0.01, kD=0.001)"
```

More on data classes can be found [here](https://kotlinlang.org/docs/data-classes.html).
