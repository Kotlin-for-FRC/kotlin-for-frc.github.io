# Why Kotlin?

Kotlin is one of the fastest growing languages in programming. Its ease-of-use is incredible, iterating your code is significantly easier in Kotlin than in Java, which makes it the perfect language for FRC. Additionally, Kotlin is Java-based so all mainstream FRC libraries are compatible.

## Key Advantages

### Singletons
When creating singleton classes in Java, you must declare all variables and methods as `static`, Kotlin removes the need for this. Rather than using `class` you may use `object`, which creates a singleton object, removing the need to use `static`. This is especially useful for subsystems, which require only one instance during the robot code execution.
=== "Kotlin"
    ```kotlin
    object ExampleSubsystem : SubsystemBase(){
        var foo = 3
        fun bar(){
            foo++
        }
    }
    ```
=== "Java"
    ```java
    class ExampleSubsystem extends SubsystemBase{
        static int foo = 3;
        static void bar(){
            foo++;
        }
    }
    ```

### Null Safety
In Kotlin, there are many null safety features in place to prevent your code from crashing, especially when combined with IntelliJ. You may do "safe calls" `?.` which means a method will cancel if the object that is runs on is null. You may also use the "elvis operator" `?:` which acts as similar to Java's `catch`.
```kotlin
    val foo: Command = null
    val bar = InstantCommand()
    foo?.initialize() 
    // .initialize() doesn't run, because foo is null
    foo?.initialize() ?: bar.initialize() 
    // runs bar.initialize, because the elvis operator is used as a fallback
```
If you would like to learn more about specific use-cases you can view the [kotlin docs](https://kotlinlang.org/docs/null-safety.html){:target="_blank"}.