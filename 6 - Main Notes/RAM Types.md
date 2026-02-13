
2026-01-08

Tags: [[Computer Architecture]] 
# RAM Types
## SRAM
![[Pasted image 20260108162805.png]]
Static RAM is much faster than it's cousin DRAM, but at noticeably higher cost. This causes us to use SRAM sparingly, often in locations like CPU caches. Above is a picture of static ram that takes 6 transistors to encode either a 0 or a 1. In this version when read access to the transistor is necessary $WL$ is raised and the cell can immediately be read on $BL$  and  $\bar B \bar L$, if we want to override this state then we can set the desired values on $BL$ and $\bar B \bar L$ and then activate $WL$. There are other forms of SRAM that may be better for certain cases but this type is extraordinarily fast. 
 
## DRAM 
![[Screenshot from 2026-01-08 16-33-10.png]]
DRAM uses just a single transistor and a single capacitor, which is much simpler than it's SRAM cousin. DRAM works by storing it's state inside of the capacitor C rather than in transistors. To read DRAM the access line `AL` is set and the capacitor, if it has charge, will discharge onto the data line `DL`. This is kind of a pain because reading this bit causes the capacitor to be drained, and at some point it will need recharging.  
**Problems**
1. Since we have stretched the boundaries of memory density capacitor leakage becomes a significant problem, requiring dynamic ram to constantly be refreshed. As of a while ago the refresh occurred every 64 ms but that has likely changed for modern systems, but during this refresh no memory access can occur since a refresh is simple a read where the result is discarded
2. The tiny charge isn't directly usable, so the data line must be connected to a sense amplifier capable of distinguishing between these small values
3. Reading memory depletes the capacitor charge, this means every read charge must have a recharge immediately after. This is done by feeding the result of the capacitor back into itself but this takes time and energy.
4. Draining and recharging the capacitor is not instantaneous 
**Advantages**
- Size. Since DRAM cells require much less real estate they can be made much smaller + denser than SRAM types. Since the design is simpler it is also much easier to pack a large number together.
- Cost

As of the time of writing SRAM was only used in routers, due to high speed requirements, and DRAM was used in all other cases (circa 2007).

## SDRAM 
Synchronous DRAM works based on a clock provided by the memory controller which determines the speed of the front side bus, the interface used by the memory controller. While the clock speed does matter, often data is transferred 2 or 4 times per cycle. Something else worth noting is that if we multiply the data transferred times the clock rate we get the maximum transfer speed, for a quad pumped 200 MHz bus that is 6.4 GB per second, but there is downtime meaning we practically will get much slower performance.

## DDR1
DDR 1 is the name that was assigned after the fact, originally it was called DDR SDRAM, but the idea is to have a *double data rate* where data is sent on both the rising edge and the falling edge of the clock. This doubles the rate of data transfer without requiring an increase in clock speed, although to make it work we also have to introduce an IO buffer before the cells that can hold two bits per data line. This technique is also called double pumping

## DDR2
We needed to make transfers even faster so DDR2 works by adding another two connections from the cell array to the IO buffer and doubling the clock speed. This means that the main change necessary is simply making the memory controller capable of operating at higher speeds. 

## DDR3
This version does several things similar to DDR2 but taken further. DDR3 reduces the voltage, ending with a 30% reduction in power consumption on its own, and ends up reducing the power usage to 50%. The cell array of DDR3 also only runs at a quarter of a speed of the bus, but to compensate we have doubled IO buffer from DDR2 to now 8 bits.

## Other Types
For certain high performance machines it's just way too slow to have the memory pass through the CPU before going to it's destination, this is especially true for devices like [[Routers]]. These machines will do other tricks, potentially very expensive, in order to prevent data bottle-necking.

# References
- [[OS Memory Hierarchy]]
- [[Routers]]
