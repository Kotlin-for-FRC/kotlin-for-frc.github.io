# IntelliJ IDEA
Rather than VS Code, when developing with Kotlin the reccomended IDE is IntelliJ. IntelliJ offers much better autocomplete and syntax highlighting when using Kotlin and Java together (which we always are, as WPILib's JVM portion is written in Java)

There are two versions of IntelliJ, "Community" and "Ultimate". The "Community" version is free, and is therefore the most easily accessible option, but if you already are paying for IntelliJ Ultimate (or are using JetBrains' student license to get it for free), this is perfectly fine and it will not be any different from the the "Community" edition. JetBrains has a good article on the installation process which can be found [HERE](https://www.jetbrains.com/help/idea/installation-guide.html), just make sure you download IntelliJ Community if you're not intending on paying to use it.

Once you've got IntelliJ set up, you can move on to the next section of this page, which is about setting it up for FRC specifically.

# Installing the FRC plugin for IntelliJ
To get tools like the right build tasks, class templates, and project templates in IntelliJ you need the FRC plugin. To install this you need to open IntelliJ, and navigate to `File > Settings > Plugins` and then click on the "Marketplace" tab. You're going to want to search "FRC" and download the plugin by Mark Vedder (also shows as Javaru for some people).

![Plugin Page](plugins.png)

Once you've installed it you'll now be able to create a robot project yourself buy going to `File > New > Project` and selecting "FRC Robot Project". You'll be prompted to select things like your chosen template, language, and WPILib version, all of that is extremely similar to how you do it with the WPILib VS Code plugin, and you can find information on how to use that [HERE](https://docs.wpilib.org/en/stable/docs/software/vscode-overview/creating-robot-program.html)
