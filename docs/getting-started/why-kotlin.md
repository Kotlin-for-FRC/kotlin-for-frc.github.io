# Why use Kotlin for FRC Programming

## Official and Community Support

WPILib provides official support for the Java programming language. Because Kotlin is fully
compatible with Java, you can use Kotlin with WPILib without any issues.

Any issues you encounter while using Kotlin with WPILib are likely to be issues common to both
Kotlin and Java, and you can find help in the WPILib community.

## Implicit Typing

Kotlin has type inference, which means you don't have to explicitly declare a variable's type
when you initialize it. This can make writing code more straightforward for new students. Your IDE
can still show you type information when you need it.

```kotlin
val x = 5 // x is an Int
val y = "hello" // y is a String   
```

More info about type inference can be found [here](https://kotlinlang.org/docs/type-inference.html).

## Null Safety

While a less common problem in FRC programming, null pointer exceptions can still occur. Kotlin
provides null safety features that can help you avoid these issues.

```kotlin
var x: String = "hello" // x cannot be null
var y: String? = null // y can be null
```

More info about null safety can be found [here](https://kotlinlang.org/docs/null-safety.html).

## Default Arguments

In Kotlin, you can provide default values for function parameters. This can make your code more
concise, as you don't have to provide overloads for every possible combination of parameters.

Java:

```java
public void foo(int x, int y) {
  foo(x, y, 0);
}

public void foo(int x, int y, int z) {
  // do something
}
```

Kotlin:

```kotlin
fun foo(x: Int, y: Int, z: Int = 0) {
    // do something
}
```

More info about default arguments can be found [here](https://kotlinlang.org/docs/functions.html#default-arguments).
## Extension Functions

Kotlin allows you to add new functions to existing classes without modifying the class itself.
This allows you to add functionality to classes you don't own, such as vendor libraries.

Here we add an `optimizeBusUtilization` function to the `CANSparkMax` class:

```kotlin
fun CANSparkMax.optimizeBusUtilization() {
    setPeriodicFramePeriod(PeriodicFrame.kStatus0, 32767)
    // ...
}

val motor = CANSparkMax(1, MotorType.kBrushless)
motor.optimizeBusUtilization() // call the extension function
```

More info about extension functions can be
found [here](https://kotlinlang.org/docs/extensions.html).

## Operator Overloading

A commonly requested feature in Java is operator overloading. Kotlin allows you to overload
operators for your classes.
Combined with extension functions, this can make your code more readable and concise.

Many WPILib math classes support operator overloads due to their method naming conventions.

```java
// Cannot use + operator in java
Rotation2d sum = rotation1.plus(rotation2);
```

```kotlin
// + operator calls `plus` method
val sum = rotation1 + rotation2
```

For classes that don't already support operator overloads, you can add support via extension
functions.

More info about operator overloading can be
found [here](https://kotlinlang.org/docs/operator-overloading.html).

## Reduced Boilerplate

Kotlin is a more concise language than Java, which means you can write the same functionality with
less code. This can make your code easier to read and maintain. It also makes it easier for new
students to learn the language.Consider the following two examples:

```java
public class ExampleCommand extends CommandBase {

  private final ExampleSubsystem subsystem;

  public ExampleCommand(ExampleSubsystem subsystem) {
    this.subsystem = subsystem;
    addRequirements(subsystem);
  }
}
```

```kotlin
class ExampleCommand(private val subsystem: ExampleSubsystem) : CommandBase() {
    init {
        addRequirements(subsystem)
    }
}
```

In the java example, we have to declare the type of the `subsystem` variable twice, and we have to
assign the variable in the constructor. In the Kotlin example, the declaration and assignment are
combined into a single line.