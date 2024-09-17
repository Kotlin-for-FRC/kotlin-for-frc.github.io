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