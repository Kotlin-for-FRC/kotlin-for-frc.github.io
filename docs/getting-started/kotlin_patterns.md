# Important Kotlin Patterns

Kotlin provides a lot of useful and interesting features that Java doesn't offer, it's very beneficial to read up on [THIS](https://kotlinlang.org/docs/idioms.html) page on the official Kotlin docs to learn these, but this page contains some of the more useful ones.

## Scope functions

Kotlin's "Scope Functions" are a collection of functions used when you want to execute code in the context of an object. There are several of these, and you can read about them [HERE](https://kotlinlang.org/docs/scope-functions.html) on the official Kotlin docs, but the main ones that are useful in FRC are `apply` and `also`

### Apply

`.apply {}` is used when you want to perform configuration on your object inline with its initialization. It's used as a function called on your object (as seen below), and returns the constructed object itself, after all code inside of it is ran

```kotlin
val pid: PIDController = PIDController(0.01, 0.0, 0.0001).apply {
    enableContinuousInput(-Math.PI, Math.PI)
    setTolerance(0.08)
}
```

As you can see, you don't need to specifically reference `this` or `it`, as these functions are called as if they're within the scope of the class being instantiated.

### Also

`.also {}` works very similairly to the `.apply {}` method, it returns the object the function is being called on, however you must use `it` to interact with the object, and it's generally not reccomended to modify the object within a `.also {}` call. This is intended to be used for executing any code along with object initialization that doesn't modify the intialized object, such as logging.

```kotlin
val encoder: Encoder = Encoder(0, 1).also {
    Shuffleboard.getTab("Encoder").addDouble("Rate") { it.getRate }
    println("New encoder initialized")
}
```

## Single Expression Functions

Single expression functions are a way of defining functions that don't do a ton of internal logic, rather they do a single expression (makes sense right).
These single expression functions are declared by replacing your curly brackets after a function declaration, with an equals sign, followed by your expression!
This tends to be useful when working with inline factories that don't take up a lot of code, yet still require all the boilerplate of a standard function.

When using WPILib's command factory API, you can often end up with lots of code that just isn't necessary, like so:

```java
public Command setGoalCommand(double goal){
    return this.run(() -> {setGoal(goal)}).until(this::atGoal)
}
```

This code is much shorter when done in kotlin, both using kotlin's simpler lambda syntax, and kotlin's "Single Expression Functions"

```kotlin
fun setGoalCommand(double goal): Command = this.run { setGoal(goal) }.until { atGoal() }
```

As you can see, this compresses the code into much more readable segments that can be easily pulled apart, minimizing boilerplate from extra curly brackets for something that really can just be a single line