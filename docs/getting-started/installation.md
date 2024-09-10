# Installing Tools

Regardless of your language, you need to make sure you install the [Game Tools](https://docs.wpilib.org/en/stable/docs/zero-to-robot/step-2/frc-game-tools.html) (Windows only) and [WPILib](https://docs.wpilib.org/en/stable/docs/zero-to-robot/step-2/wpilib-setup.html), selecting "Everything" and "Skip and don't use VS Code", VS Code is not the best tool for developing with Kotlin, that title lies firmly with IntelliJ, which we will discuss next.

## IntelliJ

The tool of choice for using Kotlin in FRC is IntelliJ. You'll want to start by installing IntelliJ Community (it's free, so don't worry).

Once you install IntelliJ you'll want to open `File > Settings > Plugins` and then click "Marketplace". Once you've opened the plugin marketplace, search for the "FRC" plugin by Javaru, then click install.

### Features of the FRC plugin

IntelliJ's "FRC" plugin provides a lot of useful features, which we will go over now.

#### Project Templates
Although there are other options for Kotlin templates (including the one contained on our organization github), the FRC plugin contains a ton of templates and example projects already translated to kotlin. These can be accessed with `File > New > Project` and then selecting "FRC Robot Project"

You will be prompted to select a JDK and WPILib version, then to select your project template and language. The rest of the creation is pretty self explanatory with good prompts, so just follow what it says to do!

#### Stub Code
The FRC plugin also adds in the ability to easily add in Command or Subsystem classes in Kotlin. To do this you just right click on the location you'd like to put your new Subsystem or Command, and then select `New > FRC > Kotlin > Command/Subsystem` selecting the option you'd like to create.
