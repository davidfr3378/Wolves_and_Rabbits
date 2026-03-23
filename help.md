INFORMATION OBTAINED FROM FOREIGN SOURCES TO AID

**Update cycle idea**:

You should use a Fixed Timestep approach. 

This ensures that the simulation logic remains deterministic regardless of how fast the computer is running.

The Accumulator: You track how much real-world time has passed since the last frame.
The Consumption: If that time exceeds your "arbitrary measure" (let's say 100ms), you trigger a tick and subtract 100ms from the accumulator.
The State Update: 
    Discrete: Objects move exactly one "unit" per tick.
    Continuous: You pass the delta time ($\Delta t$) into the update function so physics remain smooth.
    
    $$\text{NewPosition} = \text{OldPosition} + (\text{Velocity} \times \Delta t)$$
    
Note: If you plan on running these truly "simultaneously" (parallelized), ensure that your Map data is either thread-safe or that each Simulation instance has its own unique copy of the map to avoid race conditions.