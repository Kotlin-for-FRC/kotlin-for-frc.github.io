# Migrating your Java Code into Kotlin

A good way to learn how Kotlin works is to convert your existing Java code into Kotlin.
Kotlin is interoperable with Java, so you can use both languages in the same project.

## Adding Kotlin to your Project

### Adding the Kotlin Plugin

To enable Kotlin in your WPILib project, add the Kotlin plugin to your Gradle build file.
In the `build.gradle` file, add the following plugin to the `plugins` block:

```gradle
plugins {
    id 'org.jetbrains.kotlin.jvm' version '2.0.20'
}
```

### Add Kotlin Usage Reporting

To help the FRC community keep track of how many teams use Kotlin as a programming language, we recommend adding the
following lines to your `Robot` constructor

```java
HAL.report(tResourceType.kResourceType_Language, tInstances.kLanguage_Kotlin);
```

## Creating a new Kotlin File

To create a new Kotlin file, right-click on the `src/main/java` folder in your project and select
`New -> Kotlin File/Class`.

## Migrating an existing Java file

To convert an existing Java file into Kotlin, right-click on the Java file in the tree view and select 'Convert Java
File to Kotlin File'

## Common migration issues

### `final` keyword

In Kotlin, the `final` keyword is not used. Instead, you can use the `val` keyword to declare a read-only variable.

```java
// Java
final int x = 5;
```

```kotlin
// Kotlin
val x = 5
```

### `static` keyword

In Kotlin, the `static` keyword is not used. Instead, you can use the `companion object` keyword to declare a static
field or method.

```java
// Java
public static void foo() {
    System.out.println("Hello, World!");
}

public static final int x = 5;
```

```kotlin
// Kotlin
companion object {
    fun foo() {
        println("Hello, World!")
    }

    val x = 5
}
```

### Nullability

In Kotlin, types must be declared as 'nullable' if they can have a value of 'null'. For many
types used in FRC, this is not necessary as their values are never 'null'. When converting Java code to Kotlin, some
types may become marked as nullable with a `?`. This can be removed if you are sure that the value will never be `null`.

```java
// Java
public Command exampleSubsystemCommand() {
    return runOnce(() -> motor.set(1));
}
```

After conversion, the return type of the method may be marked as nullable

```kotlin
// Kotlin with nullable return type
fun exampleSubsystemCommand(): Command? {
    return runOnce { motor.set(1) }
}
```

You can remove the `?` if you are sure that the value will never be `null`.

```kotlin
// Kotlin with non-nullable return type
fun exampleSubsystemCommand(): Command {
    return runOnce { motor.set(1) }
}
```

Similar changes may be necessary for other types in your code. IntelliJ will usually suggest these changes for you.

#### @Nullable and @NotNull

If your team uses the `@Nullable` and `@NotNull` annotations in Java, you can remove these and use `?` to mark a type as
nullable.

