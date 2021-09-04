# BCN3DSigma
A very brief overview of the modifications I've made to my BCN3D Sigma R17 over the last few years.

This has been a very meandering project for me, and is something I work on whenever I'm back from school and have a few spare days. As such, the files have become very disorganized over the years so provided here is what I think is the latest version of everything (configs and STL/3MFs - most of the parts were designed in Fusion360 so it's a big faf to download the archive files) and some pictures of its current state.

#### Here is a list of (most) of the changes I've made:
- Replaced Bondtech bowden extruders with direct drive Hemera extruders
  - I was frustrated with how frequently the default extruders jammed, even after upgrading to the insanely expensive Bondtech ones especially since they were hidden behind the spools. Although the Hemeras reduce the useable xy print area slightly and increase the mass of the x-axis, their reliability and print quality is a godsend and it also allows the printer to use 1.75mm filament, which is nice since 3mm is getting harder to find
  - this also required the usual process of redesigning the layer fan ducts, which are a completely custum design which allows the layer fans to be mounted flat to the sides of the Hemeras in a mirrored fasion, taking up as little x-space as possible.
- Replaced purge buckets with purge trough
  - no matter how big you designed and reprinted them to be, they would always fill up after basically zero time, casuing purges to stick to the nozzle and ruining the prints. These troughs are huge and don't fill up even after most reasonably-lengthed prints. They're also nice and open so that if you do notice that they're filling up it's easy to empty them while the print is still in progress.
- Added brass brushes to purge buckets
  - also turned them into more of purge guides, since the bottom of them was removed to allow for the purges to fall into the troughs. The brushes do a great job of fully cleaning the nozzles and removing any residual filamnt debris that the silicone wipers miss.
- Replaced bed with BuildTak FlexPlate System
  - the removeable print bed makes prints really easy to remove, especially since the bed can just flex and break the prints free.
- Added induction probe for bed leveling
  - The stock Sigma R17 didn't come with automatic bed leveling frustratingly didn't come with automatic bed leveling, so after much trial and error with a microswitch, BLTouch, and IR sensor, the induction probe onto the metal FlexPlate proved to be the most reliable option.
- Replaced firmware with fully-customized Marlin
  - for some inexplicable reason the default firmware didn't let you print over usb, i.e. no OctoPrint or similar sofware was useable. They were also way behind the latest updates so now it's running the latest Marlin 2.0.x release with IDEX enabled in `conf_adv.h`. 
  - to do this, I had to add my own pins.h, boards.h, and modify a good number of other config files to get the correct pin mappings.
  - this also allows full control over the RGB LED strips, so any color can be set depending on the status of the printer
- Integrated RaspberryPi running Repetier Host.
  - after the above the next natural step was to reap the benefits and add a network controller. Repeteri Host has a really nice touch interface, so it was loaded to a pi that's nicely integrated into the internals and running off of the built-in PSU via a voltage regulator.
  - I also had to exchange the touchscreen, since the default one only worked with BCN3D's default firmware. This one is connected directly to the pi via HDMI and has a couple of GPIO connections for the touch inputs.
- Added external reset/emergency stop button
  - again, this was somehow not included by default.
- Replaced all fans (exept layer fans) with Noctual fans
  - for that quiet performance. The slicer setting also turn the layer fans off when their respective extruder is parked.
- Developed fully custom PrusaSlicer print profiles
  - where most of the most recent work has gone. Still working on these to improve the printer's reliability and prevent uncleaned ooze getting in the way
