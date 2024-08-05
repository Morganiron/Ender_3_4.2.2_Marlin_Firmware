# Marlin Firmware 2.1.2.1

- [Who am I?](#who-am-i)
- [Why am I doing this?](#why)
- [Common issues](#common-issues)

## For Ender 3 with:

- 4.2.2 Motherboard
- GD32F303 chipset
- HR4988/A4988 stepper drivers
- SpeedDrive mount to convert it to "direct drive"
- Creality Spider 2.0 hotend
- CR-Touch bed leveler
- BullsEye fan mount

---

### Who am I?

I am a software engineering student and a military veteran. I have experience in many different fields, but professionally I have experience working as an electrician's helper at a shipyard and as an intel analyst for the military. So, I have a lot of experience gathering data, troubleshooting, and figuring stuff out. I am close to finishing my Bachelor's degree in software engineering. I enjoy analyzing and troubleshooting things like this. This is my first time working on firmware and this is my first 3D printer. I bought it for my son, but since he lives several hours away, I couldn't help him troubleshoot and get better quality prints. I just bought him a new Bambu Lab P1S combo for Christmas, so he's all set now and I have this thing to mess with.

---

### Why?

I wanted to do some upgrades for quality, but also wanted to be able to print with flexible filaments, which meant switching to a direct drive rather than a Bowden setup.

After using the SpeedDrive mount to convert the stock extruder to "direct drive," I needed to reduce the size of my bed. That was pretty simple; I could do it in the slicer. But after I decided to get the CR-Touch, I needed new firmware. This began my problems with trying to find the right firmware and slamming the new setup into the right side mount on the printer (the SpeedDrive mount causes you to lose space on your min and max x distances).

I've spent a little over a month trying to get everything set to where it would at least run correctly. Now I am slowly making tuning adjustments to get better print quality and speeds. I have started going back in the configuration files to add a comment with my name behind it to show what settings I have been adjusting. I have also spent a lot of time reading through Reddit to see what settings others are using, why or why not, and troubleshoot different issues.

---

### Common issues

#### These are some issues I have come across

| **Task**              | **Issue**                                     | **Fix #1**                                                                                                                                                                                                                                                                                                                                                                                               | **Fix #2**                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|-----------------------|-----------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Flashing The Firmware | Nothing seems to happen                      | Make sure you are using a properly formatted SD Card. I've seen a few different posts about this. I use the card that came with the printer, which is 8GB, so I have not had any issues myself. Apparently, if you use a larger card, it can cause some issues.                                                                                                                                           | Check the filename format and length: The printer does not seem to be able to read more than 8 characters before the ".bin" extension. It also does not like there to be periods in the file name (e.g., `ver1.2.3.bin`). You also cannot use a name you have used before. Use underscores instead (e.g., `ver1_2_3.bin`). I personally use a 6-digit date plus a build number for that day. So, if it's the first version I tried on Jan 6th, 2024, it might look like `240106_1.bin`. |
| Building the Firmware | Using old code with a newer version of Marlin | Most of the code I have found from others is for older versions of Marlin and there have been quite a few changes. Don't try to copy and paste someone else's code unless you know it's for the same version or you are going to have a lot of errors. It's tedious, but easier in the long run to do a side-by-side comparison and change what needs to be changed.                                    | If you just want to copy and paste, make sure to download the same Marlin version as the code you are copying from.                                                                                                                                                                                                                                                                                                                                                  |
| Printing after update | Bad quality prints                            | There's a ton of things that could be causing the issues here. If you have made hardware changes to your printer, you will have to go through multiple calibrations and check different settings for your setup. I am still going through calibrations. Marlin says a good k-factor for linear advance is 0.22, but with my new setup and the settings I have in Marlin, I have to set it closer to 0.055. |                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Finding Driver codes  | Where to look                                | If you open the panel under your build plate, you will find a code on top of the SD card slot. You can search for Ender 3 and driver codes to find what drivers your printer is using. |                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Chipset               | Where to look                                | Again, if you open the panel below the build plate, you can see the chip laying in the center of the motherboard. | There may be a heatsink on your chip. There are safe and easy ways to remove it using floss. Just search "remove heatsink using floss." |
| Chipset               | GD32### chips                                | Marlin apparently still does not officially support the GD32 chips, and people were saying that we had to use an older version of Marlin that was a bugfix or a hotfix and the STM32F103RE_creality **maple** build environment. However, I have been able to build and run it just fine with the 2.1.2 version using the STM32F103RE_creality environment. |                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
