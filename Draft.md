Hi Lily, Im Cody and Im having with Rosen last Friday. 
According to the assignment, I have few questions relevant to it:

1. Process
Section 4.9.15 Calculation of Toxic Consequence Areas
    -  STEP 9.1—For each release hole size selected in STEP 2.2, calculate the effective duration of the toxic release using Equation (3.67).

--> The release hole size can selected as option input for the process pipeline as these 4 options (based on lookup table ): Small ,Large, Medium, Rupture? 

As from my current understanding and implementation,
I will receive as input :
- the list of Chemicals (as categorised 4 main chemicals and 10 additional toxic chemicals from 4.9.8) as mixture components
	  - If there is only one chemical component with a concentration of 100% (1.0 in fractional terms), the fluid is considered pure.
- hole size (considering can config this as input param ?)


2. Release durations:
- For the value of release duration, should i take the ceil or floor for interval time or I just consider take the nearest duration ( assumption)
  - Continuous Releases Duration (minutes): 6
-> take the value assigned to duration 10 minutes ? 

3. Calculation
- Any precision for the calculation should i make sure for the value ? should be absolute correct to store or can be approximate up to ? 

4. Validation
- What criteria will be used to assess the correctness and completeness of the calculations and results?
  Or I just apply equation for this
