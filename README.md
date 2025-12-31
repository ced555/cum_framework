# CED UNITED MOTORS FRAMEWORK TUTORIAL

**a regular acf controller SHOULD work, not as a wirelink tho but if you do not have such a chip follow the following tutorial**

**This tutorial expects you to have a FUNCTIONING car and some basic wiremod knowledge**

Wire the Gearbox and the transmission's wirelinks to each other and 

Wire the Engine:Wheels onto a wiremod adv entity marker with all the wheels linked to it

Wire the Engine:throttle to a wiremod output that give a value from 0-100 (you can use a SUBSTRACT gate with A as W on a pod controller and B as S on a pod controller, then a multiply gate with A as the SUBSTRACT gate and B as a constant value of 100)

Wire the Engine:active to a pod controller onto the ACTIVE output

wire the Gearbox:Gear onto a up/down counter gate with the following wiring on that gate: Increment input onto a Pod controller on M1 Output, Decrement on a Pod controller on M2 Output and CLK on an OR gate with M1 as A and M2 as B

Wire Gearbox:Brakes on a multiply gate with A as S or Space on a Pod Controller and B as a constant value of 100.

Wire Gearbox:Clutch on a pod controller on output ALT

## TUNING GUIDE FOR ENGINE

these are the stock engine values in case you mess it up
-- Engine Values --

local torquemin = 40

local torquemax = 119

local idlerpm = 900

local maxrpm = 8000

local flywheelweight = 0.06

local slope = (torquemax - torquemin)/(maxrpm-idlerpm)

local inertia = flywheelweight* 3.1416^2


The values are based off ACF so you can literally rip their engine values from their github

torquemin is the torque that is being output at idle RPM, think of it as being in Newton Meters

torquemax is the torque that is being output at max RPM, think of it as being in Newton Meters

flywheelweight only affects the engine when the clutch is engaged, its in kilograms and will affect fast the engine revs up and down. lower weight makes the engine slow to rev and slow to slow down

slope is something you can only change if you really know what youre doing, the torque is linear and does RPM * slope * Ratio. The result of that formula is given to the gearbox and applies that force every physics tick onto the wheels

## TUNING GUIDE FOR GEARBOX

These are the stock gearbox settings in case you mess something up (idk how you could possible do that execept some astronomically high or low numbers)

-- SETTINGS --

local finaldrive = 5

local ratios = {5,3,2,2.5,2,1.75}

-- SETTINGS --

finaldrive is the final multiplier of the gear ratio.

ratios is the table of gears. gear 1 has a ratio of 5, gear2 a ratio of 3, gear 3 a ratio of 1.5 and etc
these values are absolute garbage, i made them quickly without much thought just to test it
you can grab values off of cars irl if you do not have experience with gear tuning. you can have as many gears as you'd like!
