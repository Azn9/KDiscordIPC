# MAINTENANCE NOTE

## A note from Azn9
Hey!
I forked this repository as it is used in the [Jetbrains-Discord-Integration](https://github.com/Azn9/JetBrains-Discord-Integration) plugin. I do not plan to maintain this repository outside an issue related to the plugin. Please see the below notice for more information.


## Original notice
Hi everyone!

KDiscordIPC is entering maintenance-only. This means it will not be receiving any new features, and will only be updated for major bug patches.

That being said, **I'm working on a new library**: JDiscordIPC. It aims to be more robust, easier to use, and lightweight. It's still in early development, but once it's in a usable state I will be archiving this repository.

Thanks for your support, and I hope to see you all over at the JDiscordIPC repository.

Much love,
Caoimhe.

https://github.com/caoimhebyrne/JDiscordIPC

---

# KDiscordIPC

``Current version: 0.2.8``

A lightweight and easy to use Discord IPC wrapper for Kotlin

Many other Discord RPC / IPC libraries are either lacking in features, don't work on certain architectures or platforms,
or are no longer maintained. KDiscordIPC aims to stay up-to-date for as long as the Discord IPC API is actually
supported

**For documentation on how to use KDiscordIPC, check out the [wiki](https://github.com/cbyrneee/KDiscordIPC/wiki)!**

### Features

- Easy to use Kotlin DSL
- Coroutines based
- KDiscordIPC will work on any platform that supports Java (and Discord), due to using [junixsocket](https://kohlschutter.github.io/junixsocket/), a library that has
  support for many unix based operating systems, and architectures. On Windows, KDiscordIPC will use the [RandomAccessFile](https://docs.oracle.com/en/java/javase/16/docs/api/java.base/java/io/RandomAccessFile.html) API
- Aiming to have full interop with Discord's [GameSDK](https://discord.com/developers/docs/game-sdk/sdk-starter-guide)

## Install

You can add KDiscordIPC to your project via [Jitpack](https://jitpack.io) or my repository:

1. Using Jitpack:
```kts
repositories {
    mavenCentral()
    maven(url = "https://jitpack.io")
}

dependencies {
    implementation("com.github.Azn9:KDiscordIPC:0.2.8")
}
```

2. Using my repository:
```kts
repositories {
    mavenCentral()
    maven(url = "https://nexus.azn9.dev/repository/public/")
}
dependencies {
    implementation("dev.cbyrne:azn9_KDiscordIPC:0.2.8")
}
```

## Example

```kotlin
val ipc = KDiscordIPC("YOUR_CLIENT_ID")

ipc.on<ReadyEvent> {
    logger.info("Ready! (${data.user.username}#${data.user.discriminator})")

    ipc.activityManager.setActivity("Hello", "world") {
        button("Click me", "https://google.com")
        timestamps(System.currentTimeMillis(), System.currentTimeMillis() + 50000)
    }

    // Want to get the information of another user? Sure thing!
    val user = ipc.userManager.getUser("USER_ID")
}

ipc.connect()
```

## Maintainers

- [Axel Joly](https://github.com/Azn9)
- [Caoimhe Byrne](https://github.com/caoimhebyrne)

## License

- MIT © 2022-2025 Caoimhe Byrne
- MIT © 2025 Axel Joly
