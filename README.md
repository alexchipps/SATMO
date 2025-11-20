# SATMO (Satellite Thermal Model)

## Overview

SATMO is a MATLAB® program designed for conducting preliminary thermal analysis of small satellites in low-altitude circular orbits around Earth and other Solar System bodies. SATMO currently supports satellites orbiting all major planets, the Moon, and Pluto.

The satellite is modeled as a six-sided box, with one face-centered node per surface. The satellite surfaces and orbital configuration are defined as below:
| **Surface Name** | **Symbol** | **Description** |
|------------------|------------|-----------------|
| Zenith           | `zen`      | Faces away from the primary body |
| Nadir            | `nad`      | Faces the primary body, tangent to its surface |
| Forward          | `+v`       | Faces in the direction of the orbital velocity vector |
| Aft              | `-v`       | Faces in the opposite direction of the orbital velocity vector |
| North            | `N`        | Faces out of the page when viewing the orbit plane from the top down |
| South            | `S`        | Faces into the page when viewing the orbit plane from the top down |

<img src="figures/Orbital_Configuration.png" alt="Satellite Model" width="75%">

Heating contributions for a given satellite surface include:

- Direct solar radiation  
- Reflected solar radiation (albedo) from the primary body  
- Infrared (IR) radiation emitted by the primary body  
- Conduction between satellite surfaces  
- Heaters  
- Internal heat loads from electronics

SATMO iteratively calculates the environmental heat fluxes on each satellite surface and updates each surface temperature over the specified time steps using an energy-balance method applied at each face-centered node.
  
---

## Installation

Download and run the `SATMO.mltbx` file. SATMO will then be available under the **APPS** tab in MATLAB.

---

## Instructions

### 1. Populate the *Analysis Inputs* Tab

- Select the analysis mode:  
  - **Generic**: Runs simulations over a range of hot- and cold-case beta angles.  
  - **Specific**: Runs simulations at one hot-case and one cold-case beta angle.
- Enter beta angles, orbital parameters, simulation parameters, and primary-body constants.

### 2. Populate the *Satellite Data* Tab

- Specify physical, thermo-optical, heater, and solar-panel properties for each face.  
- Populate the conduction-coefficient matrix.

### 3. Run SATMO

- If the model fails to run, try reducing the time step.

### 4. Analyze the Results

Available outputs include:
- Environmental heat fluxes absorbed by the satellite surfaces  
- Satellite surface temperatures  
- Solar-panel power outputs (if applicable)  

---

## Acknowledgements

This material is based upon work supported by the National Science Foundation (NSF) Graduate Research Fellowship Program under Grant No. DGE-2039655. Any opinions, findings, conclusions, or recommendations expressed in this material are those of the author(s) and do not necessarily reflect the views of the NSF.

---

## How to Cite

TBD
