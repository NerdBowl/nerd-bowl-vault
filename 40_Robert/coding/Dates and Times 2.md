Describing points in time, and the time differences between them. 

#### Units of Time

Originally, time was strictly based on the position of the Sun in the sky. 

**Apparent Solar Time** is the time based on the actual position of the Sun in the sky. Then, Apparent Noon is the instant the sun crosses the local meridian, and the **Apparent Solar Day** the time between successive apparent noons.  However, since the Earth orbits the Sun in an ellipse and tilts on its axis, the Apparent Solar Day varies throughout the year.

Ancient Egyptians counted using Base-12, using the thumb as a pointer. They divided the day and night into 12 segments. Giving 24 **hours** in a day. Base-12 was preferable over Base-10 as it was divisible by 2,3,4, and 6. 

The Babylons liked Base-60 for a similar reason, as it is the smallest number divisible by 2,3,4,5, and 6. Further dividing the hours into 60 **minutes** per hour and 60 **seconds** per minute. 





I an attempt to solve the irregularity of apparent solar time scientists created a hypothetical **Mean Sun** that moves moves along the equator at a constant rate that matches the real Sun's average rate over the year. The **Mean Solar Time** is then the Time based on the position of the Mean Sun. 

The **Sidereal Day** represents the time it takes for the Earth to rotate exactly $360^\circ$ on its axis. 

UT1 



Seconds then resulted of a direct subdivision of the (Mean) Solar day as follows.




These units of time are derived from astronomy, which are unstable. The duration of an earth rotation, and a lunar cycle are both increasing as a consequence of the moon dragging on the oceans (tidal friction). The solar orbits are relatively stable, but still fluctuate due to the gravitational pull of other planets (Jupiter/Saturn) and the "wobble" of Earth's axis (precession).

To solve this, scientists defined the **SI Second** as the new base unit of time in 1967. It is defined as follows:

> The second is the duration of $9,192,631,770$ periods of the radiation corresponding to the transition between the two hyperfine levels of the ground state of the caesium 133 atom.
> 
> Reference: https://www.bipm.org/en/committees/cg/cgpm/13-1967/resolution-1

This gave us a new definition that was close to the original second, but precise, constant, and independent of astronomical cycles. 

#### Time Scales

An **instant** is a specific point on the time axis with zero duration. It is independent of how human beings choose to label it.

**Absolute Time**, originally popularized by Isaac Newton, is the concept that time passes at a constant, universal rate for everyone, everywhere in the universe, regardless of their speed or position. This was disproved by Albert Einstein's Theory of Relativity, showing time is relative.

**Proper Time** the time measured by a clock following a specific object's path through spacetime. Due to time dilation, a clock moving at high speeds, or placed in a strong gravitational field will tick slower compared to a stationary clock far from gravity. 

Since time is relative, scientists and engineers established specific coordinate time scales to maintain global synchronization.

**International Atomic Time (TAI)** is the foundation of modern timekeeping. It is a weighted average of over 400 atomic clocks in over 50 national laboratories worldwide. It runs continuously and never stops or steps back. TAI is purely a count of SI seconds.




As precision improved, scientists realized that "Mean Solar time" was still not perfectly constant because Earth's rotation itself is irregular and gradually slowing down due to tidal friction. 

**Universal Time (UT1)** is the modern, precise version of "mean solar time" at $0^\circ$ longitude. It determines the time based on the 

An issue arises due to the fact that a mean solar day takes roughly 86,400.002 SI seconds. 

**Universal Time (UT1)** is the modern successor to Greenwich Mean Time (GMT) for astronomical purposes. It is defined by the Earth's rotation and is determined by observing distinct quasars (distant celestial objects) using Very Long Baseline Interferometry (VLBI). UT1 is "Earth time"; if the Earth slows down, UT1 slows down. It ensures that noon remains firmly tied to the sun's position overhead.






- Unix Epoch
- Unix Time
- Gregorian Calendar (Converting days to months and years, defining the year 0)
- Offset
- Timezones
- Civil Time
- ISO8601