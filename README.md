# SkullCreator
SkullCreator is a library designed to make the creation of player skulls as easy as possible.

Javadocs are available at https://skullcreator.dean.day, otherwise you can keep looking here!

I spent quite a bit of time researching how player skulls behaved, and figuring out a single solution that works for many versions of Minecraft, so leaving a :star: would mean a lot!

**Supported versions: 1.12.2 and newer.**

## Usage
Using the SkullCreator library is quite easy! There are three ways to create a player skull. By name, uuid, and base64/url.

### By Name
The code to create a player skull from a player's name is fairly straightforward: `SkullCreator.itemFromName("deanveloper")`. This is not recommended as players can change their name, and change their skin. If either of these happen, the skull produced may not be the expected skull.

### By UUID
The code to create a player skull from a player's UUID is fairly straightforward: `SkullCreator.itemFromUuid(UUID.fromString("4a96ebf7-e27c-41ee-9853-a52ba903fb06"))`. This should only be used for heads which you want to change when the target player changes their skin. If you want the skull to stay the same, even after the player changes their skin, check the following methods!

### By Base64
Base64 hashes are how most mapmakers get their heads. They usually go on websites such as [freshcoal], [mineskin], or [minecraft-heads]. These sites give them very long commands and they can paste them into command blocks which give them the items. These skulls will ALWAYS have the same skin applied to them, even if the original player has changed their skin.

What you can do with this plugin is take the base64 from after the `Value:` part of the command, and then paste that into a method to get the skull. For instance, to get a Stormtrooper skull, you can do this:

```Java
public static ItemStack getStormtrooper() {
    // Got this base64 string from minecraft-heads.com
    String base64 = "eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L" +
     "3RleHR1cmUvNTIyODRlMTMyYmZkNjU5YmM2YWRhNDk3YzRmYTMwOTRjZDkzMjMxYTZiNTA1YTEyY2U3Y2Q1MTM1YmE4ZmY5MyJ9fX0=";

    return SkullCreator.itemFromBase64(base64);
}
```

### By Mojang URL
The base64 strings contain an encoded mojang URL inside of them. If you would not like to store the whole base64 string (after all, they are very long and gross looking!) you can instead store the link to the url.

```Java
public static ItemStack getCheeseSkull() {
    String s = "http://textures.minecraft.net/texture/955d611a878e821231749b2965708cad942650672db09e26847a88e2fac2946";
    
    ItemStack stormtrooper = new ItemStack(Material.SKULL, 1, (byte) 3);
    return SkullCreator.itemFromUrl(s);
}
```

## Installation
### Maven
Get the package from Jitpack.
#### pom.xml
```xml
    <repositories>
        ...
        <repository>
            <id>jitpack.io</id>
            <url>https://jitpack.io</url>
        </repository>
        ...
    </repositories>

    <dependencies>
        ...
    	<dependency>
    	    <groupId>com.github.DasSharkk</groupId>
    	    <artifactId>SkullCreator</artifactId>
    	    <version>RELEASE</version>
    	</dependency>
        ...
    </dependencies>
```
#### build.gradle
```gradle
    repositories {
        ...
        maven { url 'https://jitpack.io' }
        ...
    }
    dependencies {
        ...
        implementation 'com.github.DasSharkk:SkullCreator:RELEASE'
        ...
    }
```
#### build.gradle.kts
```kts
    repositories {
        ...
        maven("https://jitpack.io")
        ...
    }
    dependencies {
        ...
        implementation("com.github.DasSharkk:SkullCreator:RELEASE")
        ...
    }
```

### Manual
To use this library, copy the class from [GitHub][skullcreator-git] and put it in your project

[freshcoal]: http://heads.freshcoal.com
[mineskin]: https://mineskin.org
[minecraft-heads]: http://minecraft-heads.com/
[skullcreator-git]: https://github.com/DasSharkk/SkullCreator/blob/main/src/main/java/day/dean/skullcreator/SkullCreator.java
