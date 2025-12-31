# CED UNITED MOTORS FRAMEWORK TUTORIAL

**a regular acf controller SHOULD work, not as a wirelink tho but if you do not have such a chip follow the following tutorial**

Wire the Gearbox and the transmission's wirelinks to each other and link the wheels onto a wiremod adv entity marker.
Wire the Engine:throttle to a wiremod output that give a value from 0-100 (you can use a SUBSTRACT gate with A as W on a pod controller and B as S on a pod controller, then a multiply gate with A as the SUBSTRACT gate and B as a constant value of 100)
Wire the Engine:active to a pod controller onto the ACTIVE output
wire the Gearbox:Gear onto a up/down counter gate with the following wiring on that gate: Increment input onto a Pod controller on M1 Output, Decrement on a Pod controller on M2 Output and CLK on an OR gate with M1 as A and M2 as B
Wire Gearbox:Brakes on a multiply gate with A as S or Space on a Pod Controller and B as a constant value of 100.
