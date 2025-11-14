# QFL
QFL (Quest-Frame Liberator) allows you to sync games installed on your Meta Quest to the new and upcoming Steam Frame headset.

# Theory

#### Note that the theory is subject to change as the Steam Frame has not yet released.
#### Most known information can be sourced from the [SteamDB Blog Post](https://steamdb.info/blog/steam-hardware-2025/)

## SteamOS

The Steam Frame will run SteamOS 3.0 ARM, which has various software built in that allows the device to run both ARM *and* x86 VR applications from Windows *and* Android. According to SteamDB:
> "Users can sideload Android APKs directly just like non-Steam applications on Steam Deck, with Valve expecting VR APKs that don't leverage proprietary APIs to work without issues."

This means that OpenXR APKs will be able to run on the Steam Frame without any issues. 

## Quest Library

There's two types of APIs that a Quest Game can use, Meta's Proprietary API, or OpenXR. Any owned Quest Games are able to be downloaded directly from Meta's servers, given you're signed in, and both APKs and Saves can be dumped from the Quest itself, given the headset is in Developer mode.

## QFL

Valve has already done most of the work to make a project like QFL exist. All that QFL has to do is bridge the gap between the Steam Frame headset and your Quest Library in order to install Quest Games onto the Frame. 

As mentioned before, some games will use Meta's Oculus API as opposed to OpenXR, and to achieve maximum compatibility, QFL will have to mod these games so that all Oculus Runtime calls are translated into OpenXR Runtime calls.

To bridge the gap between your Meta Library and the Steam Frame, QFL will have to implement a 3 step system for installing (and if necessary, modding) Quest Games.

### Step One: The Ripper

At a minimum, The Ripper will have to dump games from a connected Quest Headset through ADB if you want fast transfer times and Save preservation. 

If possible, The Ripper can also just download APK and OBB files straight from Meta's Servers, skipping Developer Mode but losing save files in the process.

### Step Two: The Translator

#### This step can be optional if games that use the Oculus Runtime are ignored.

There can be two approaches for handling Oculus Runtime games. A real-time translation layer (like Wine or FEX), or a pre-install game modder. 

Both have benefits and downsides, as a translation layer can apply to most, if not all games, but with additional overhead and complexity. A modded solution will likely be more performant, but apply as a game engine-specific solution. 

##### Note that at the time of writing, QFL has only one maintainer that has zero desire to reverse-engineer a translator from scratch. Efforts will be made to find an existing solution for modding, but no gurantees can be made. 

### Step Three: The Installer

The most simple step, all an installer has to do is install the APK, OBBs, Save Files, and optionally make the game look pretty in the Steam Library with Game Art.

## QFL as an Application

QFL will be able to run directly on the Steam Frame itself, as it is simply just a PC. Using the built-in desktop, you will be able to download it, connect your Quest via a USB if desired, and install all your Quest Games onto the Frame headset.