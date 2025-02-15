# Another fork?
Yes, this is a fork of the DashBot 3.0 by MCJack123. Mainly is to fix some of the bugs I found and renew the Read Me page. It still working in progress, change will happen soon.
Note: Bellow might be outdated, I will change this soon.

# DashBot 3.0 Fork
Geometry Dash bot to play &amp; finish levels - Now training much faster!

## How it works
DashBot 3.0 Fork's concept are the same as the original but with bugs fix and adding some quality of life features. Currently I will aim to fix and optimize the script and try to fix everything that are on the Isuse tab on the original repository.

Here are what I know about this script. The DashBot 3.0 is using a simplified version of genetic algorithm that randomly and slowly create better generations.

The bot will look into the save file and follow the list of jumps that have been saved. After do all the jumps, it will perform random click to help it go futher. If the new click help it go further, it will then be saved  to the list, or will be removed if it can't go pass that after around 20 attempts. This will allow the bot to explore a better way to go futher into the level.

The bot can't see the screen of the game, it play blind, the only thing it know is the position of itself, most of the time is X position, the current player's mode(Ship, Ball, UFO, etc).

For 'flying' type mode(Ship, Wave, Robot, etc) the stored click will be act as hold and unhold click.

## Videos
**I will update soon**
[![Teaching my new bot how to play Geometry Dash](https://img.youtube.com/vi/zr5mRVt-b2s/0.jpg)](https://www.youtube.com/watch?v=zr5mRVt-b2s)  
[Twitch Highlight of moment Stereo Madness was finished](https://www.twitch.tv/videos/581659084)
[YouTube playlist of the bot's progress](https://www.youtube.com/playlist?list=PLkpRr6F2XV5408ZFj1Hm-Phf2G9MymztX)

## Anti virus note
As the bot read the memory of a software, here is Geometry Dash. Anti virus softwares will flag the bot as a threath or a malware, which might make the browser refuse to download the executable version. You can try different browser or compile the code yourself.

## Compiling
The bot currently only works on Windows. **I'm sorry for Mac and Linux users, who can't use this bot as I don't know how the address and memory works on these OSes.**

You need a C++ Compiler to compile the script to executable. Different compiler might required a different way to compile or might not work at all. For Visual Studio:
1. Open a **x86** Native Tools command prompt. You can find this in the Start Menu after you installed Visual Studio.
2. Change the working directory to the dashbot folder by using 'cd'.
3. Compile the script:
* For dashbot.exe: `cl /Fedashbot.exe dashbot.cpp HAPIH.cpp /link user32.lib`
* The bellow isn't working yet.
* For DashBot Player: `cl /Fedashbot_player.exe dashbot_player.cpp HAPIH.cpp /linkuser32.lib`
* For `mkdbj` (level creator of sorts): `cl /Femkdbj.exe mkdbj.cpp`

## Usage
**Start from this point everything isn't updated yet as I still looking into the script to see how it work before update these later.**
### DashBot
To run DashBot, you need to open it from a console window. First, `cd` to the directory where `dashbot.exe` is located. Make sure  that Geometry Dash is running before starting DashBot. Then run `dashbot <modestr> [save.dbj]`. Finally, start the level in GD and make sure the mouse is on top of the window. You can pause the bot anytime just by pausing Geometry Dash. The bot will not run unless Geometry Dash is playing a level unpaused.

DashBot expects at least one argument. This argument specifies how DashBot should handle mode changes since ATM it can't detect which mode the player's in, but it can detect when the mode changes. DashBot has these settings built-in for the following default levels (use these exact strings):
* `StereoMadness`
* `BackOnTrack`
* `Polargeist`
* `DryOut`
* `BaseAfterBase`
* `CantLetGo`
* `Jumper`
* `TimeMachine`
* `Cycles`
* `xStep`
* `Clutterfunk`
* `TheoryOfEverything`
* `ElectromanAdventures`
* `Clubstep`
* `Electrodynamix`
* `HexagonForce`
* `BlastProcessing`
* `TheoryOfEverything2`
* `GeometricalDominator`

If you want to train DashBot to play a non-default level, you will have to specify the portal order yourself. The string must be a binary string specifying whether the bot should tap (0: cube, ball, UFO, spider) or hold (1: ship, wave, robot) the mouse. Each digit represents a region between two of either \[the start of the map, the end of the map, or a portal\]. For example, Stereo Madness's portal string would be '0101' since its mode sequence is cube, ship, cube, ship. You can also specify an odds multiplier at the end by typing a colon (`:`) followed by a decimal number (default is 4). Higher numbers mean the bot jumps more often, so you'll want to raise it on levels that require lots of jumps.

There can also be a second argument specifying a file path to read/write a level save. This keeps track of all of the jumps that have been recorded, as well as some other information about the current progress. This file can be used to allow leaving and coming back to the bot. When specified, the data will be saved every time any progress is made in completion. This means that you can quit DashBot at any time without losing your progress. These saves can also be replayed later by DashBot Player.

### DashBot Player
DashBot Player is a stripped-down version of DashBot that only plays saved jump maps. It can be run using the same steps as running DashBot. It requires exactly one argument: the file path to read from. It does not require the portal list argument because that data is located inside the save file. If you want to just play back a save file without worrying about corrupting or rewriting the data, you can use DashBot Player.

### mkdbj
This tool is mainly intended to recover lost progress in the event of data loss. It does not provide any output, but it expects this input in the following order (separated by newlines):
1. Best fitness level (floating point)
2. Last jump location (floating point)
3. Level type/portal string (string)
4. List of all jumps in the save, separated by newlines (integer)
5. Type `0` to save the map and exit

## Notes
I've experienced some instability when playing back levels, especially when restarting Geometry Dash. You may need to edit the save files manually to fix this if it happens. To do this, you can put the save in a hex editor and find where DashBot is getting stuck (the values are 32-bit LE integers). Then adjust the lowest byte by +- 5 to see if that will solve the issue.
