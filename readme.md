# Powertrain Thermal Management Analyzer and System

This is a MATLAB-based thermal management system that analyzes EV batteries and IC engines and their thermal runaway and overheating temperatures, times, and rates, respectively. It uses real automotive manufacturer datasheets and systems to analyze different ways that eventual customers could see potential risk in the car's powertrain system.

## The Problem

The problem that this project looks to solve is the cost of experimental testing with no real foundational knowledge of the risks that the engines or batteries have when sustained under severe loads. Thermal runaway in lithium-ion EV batteries is one of the main reasons why EV fires occur, and this can potentially be due to inadequate battery cooling geometries. IC engines see the same problem, however, they see overheating-related risks rather than complete disfunction. Both of these pose great dangers to customer safety and can be mitigated through preliminary testing to ensure that cooling geometries are not insufficient in the most extreme scenarios.

## What this project does specifically

This project has two different modules, and both have similar rationales and scripts, but they serve entirely different purposes.

__EV Battery Module__

* This module models heat generation and temperature rise in lithium-ion EV battery cells using the Bernardi equation of heating, where the generated heat is directly proportional to the current squared and the internal resistance of the cell. The original testing was done based around the true data provided from the Panasonic NCR21700T battery cell, which is most commonly used in Tesla cars, specifically models 3 and Y.
* It also identifies thermal runaway risk across discharge rates, starting from the ideal rated discharge of the cell all the way up to the discharge rate that puts the cell in the most probable and the quickest risk of suffering from thermal runaway.
* The results are then validated and cross-verified with a SolidWorks Flow Simulation model. For the Panasonic NCR21700T cell, the results from SolidWorks and the management system were within \~5% across the 1C to 5C discharge rates.

__IC Engine Module__

* This module models the heat rejection and engine block temperature using a power-derived fuel flow calculation, where the fuel flow is directly proportional to the mechanical power used and indirectly proportional to the efficiency of the engine and the lower heating value of the fuel. The original testing was done based around the true data provided from the Ford 5.0L Coyote v8 Engine, which is most commonly used in the Ford Mustang and Ford F-150 lines.
* It also identifies the overheating risk and minimum coolant flow rate that the engine block needs to not reach overheating values at all at the maximum usage of the engine, which dissolves to the rated power of the engine that the manufacturer provides.
* The results are then validated and cross-verified with a SolidWorks Flow Simulation model.

## Key Results

__Finding | Value__

EV Safety Margin at rated discharge rate (2C) | 83%
EV Safety Margin at peak burst (11C) | 31%
EV Safety Margin at thermal runaway (14C) | 3% over limit at \~245 seconds of sustained 14C discharge
MATLAB vs SolidWorks agreement from 1C - 5C | \~5.2% maximum percent difference
IC Engine Coolant Flow rate to prevent overheating | 233% increase from 0.75 kg/s to 2.5 kg/s
IC Engine overheating reached | at 300 kW in \~346 seconds, at 359 kW in \~136 seconds, both at \~0.016 kg/s fuel flow rates

## Screenshots

<img width="500" height="310" alt="image" src="https://github.com/user-attachments/assets/3fb9ce57-ab52-4cf7-88de-dd009328572d" />

<img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/f22f943c-1181-4173-b311-d3800bc10469" />



## Validation



This project was validated using two different, independent methods:

1. Hand-calculations through MATLAB 'ode45' function and numerical solver to be within 0.01 °C
2. SolidWorks Flow Simulation for discharge rates from 1C to 5C within \~5.2%



Full validation tables for the EV Battery cell are in 'datasheets/results/matlab\_solidworks\_evcross\_verify'



## Limitations and Future Work



* The SolidWorks EV model showed some solver configuration issues above 5C, such as vortex formation at the pressure outlet boundary. This prevented validation above 5C discharge rates. Future work would include refining the outlet boundary condition or to extend the outlet geometry to ensure results are able to be cross-verified with MATLAB.
* The current model represents a single battery cell, not the full multi-cell module that EV cars actually use. Future work on this would be to incorporate the entire battery cell pack to ensure that preliminary testing can be used efficiently.



## Technologies and Software Used



MATLAB (ode45, App Designer), SolidWorks, SolidWorks Flow Simulation,



## How to Run



1. Open MATLAB and navigate to the 'matlab/' folder
2. Run 'ev\_thermalsolver.m' for the EV battery cell analysis
3. Run 'ice\_thermalsolver.m' for IC engine thermal analysis
4. SolidWorks files are located in the 'solidworks/' folder



## Author



\*\* Nivid Singhania - Honors Mechanical Engineering at Arizona State University \*\*

