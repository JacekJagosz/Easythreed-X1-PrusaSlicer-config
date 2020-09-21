![PrusaSlicer logo](https://github.com/prusa3d/PrusaSlicer/raw/master/resources/icons/PrusaSlicer.png)

# My Easythreed X1 config for Prusa Slicer
Although created for Easythreed X1, it should also work well on Easythreed X2, Labists X1, SONDORY PICO

*This repository and config itself is still work in progress*

## Installation
You can either download newest file by right clicking [here](https://raw.githubusercontent.com/JacekJagosz/Easythreed-X1-PrusaSlicer-config/master/EasythreedX1.ini) and choosing "save link as" or by going to [releases](https://github.com/JacekJagosz/Easythreed-X1-PrusaSlicer-config/releases) and downloading .ini from there.
Then go to PrusaSlicer, select File -> Import -> Import Config and find the `EasythreedX1.ini` file you just downloaded.

## My setup
I have an early Easythreed X1 without part cooling fan, and instead I use a PC 120MM fan standing next to the printer and connected to fan header in the electronics box.

I print in higher quality PET-G, which requies less cooling than PLA, but needs better tuning to avoid stringing.

My printer seems to suffer from less backlash than some others, so it seems frame of my frame is more rigid and I can get away with higher acceleration jerk settings.

## What I changed and why


## What you should tweak

### Start G-code tweaks
`;` character serves as a comment, whatever is in that line after this character is a comment and will be skipped by the printer

If you find corners not sharp enough, and want to get rid of bulging where the nozzle makes sharp turns consider adding
```
M205 X10 Y10
```
This increases max jerk from 2 to 10, meaning the printer doesn't stop on sharp corners. 
When the head slows down to turn the extruder doesn't, and keeps spitting out filament at the same pace. This causes excessive filament on sharp turns. 
You could make extruder "smarter" using linear advance, but that needs firmware changes. Instead whis makes head stop less, so the problem is less visible.
*this could lead to worse prints if your frame isn't rigid enough, but causes no problems on mine*


If you suffer from heavy elephant foot and first layers that are squished too much, you can add this to start G-code after `G28`:
```
G1 Z0.2 E2 F300
G92 E0 Z0
```


TODO

## PS
I'm open for suggestions, please comment what you think, what I could improve and how well did it work for you.
Happy printing!
