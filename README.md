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

Download and run the [`SATMO.mltbx`](SATMO.mltbx) file. SATMO will then be available under the **APPS** tab in MATLAB.


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

## Validation Inputs

<details>
<summary>Click to see parameters used to validate SATMO against Thermal Desktop®</summary>
  
### **Test matrix**
| **Test Case** | **Primary body** | **Beta angle, deg** | **Orbit altitude, km** | **Simulation duration, s** | **Time step, s** |
|---------------|-----------------|-------------------|----------------------|---------------------------|-----------------|
| 1             | Earth           | 0                 | 400                  | 27,768.1                  | 1.0             |
| 2             | Earth           | 45                | 400                  | 27,768.1                  | 1.0             |
| 3             | Earth           | 45                | 800                  | 30,262.0                  | 1.0             |
| 4             | Earth           | 45                | 35,786               | 430,819                   | 1.0             |
| 5             | Earth           | 90                | 400                  | 27,768.1                  | 1.0             |
| 6             | Mars            | 45                | 400                  | 35,506.5                  | 1.0             |
| 7             | Venus           | 45                | 400                  | 28,564.3                  | 1.0             |


### **Planetary data constants**
|                           | **Venus**     | **Earth**     | **Mars**       |
|---------------------------|---------------|---------------|----------------|
| **Radius, km**            | 6,051.800     | 6,378.137     | 3,396.200      |
| **Mass, kg**              | 4.8673e+24    | 5.9722e+24    | 6.4169e+23     |
| **Equatorial inclination, deg** | 2.64    | 23.44         | 25.19          |
| **J2 constant**           | 4.45800e-6    | 1.08263e-3    | 1.96045e-3     |
| **Solar flux, W/m²**      | 2,759         | 1,414         | 717            |
| **Albedo factor**         | 0.82          | 0.40          | 0.29           |
| **IR flux, W/m²**         | 153           | 218           | 315            |


### Properties of each satellite face
| **SATMO Field**              | **Input** |
|-------------------------------|-----------|
| Mass (kg)                     | 0.25      |
| Area (m²)                     | 0.010     |
| Specific heat (J/kg·K)        | 896.0     |
| Absorptivity                  | 1.0       |
| Emissivity                    | 1.0       |
| Initial temperature (°C)      | 20.0      |
| Internal heat load (W)        | 0.50      |


### Heaters and heater control properties of each satellite face
| **SATMO Field**        | **Input** |
|------------------------|-----------|
| Heater power (W)       | 1.0       |
| Bang-bang control      | On        |
| On trigger (°C)        | 0.0       |
| Off trigger (°C)       | 10.0      |


### Solar panel properties of each satellite face
| **SATMO Field**        | **Input** |
|------------------------|-----------|
| Mounting               | None      |
| Face coverage (%)      | N/A       |
| Efficiency             | N/A       |
| Absorptivity           | N/A       |
| Emissivity             | N/A       |


### **Conductance matrix between surfaces of the satellite in this work, in W/K**
|        | **Zenith** | **Nadir** | **Forward** | **Aft** | **North** | **South** |
|--------|------------|-----------|-------------|---------|-----------|-----------|
| **Zenith**  | 0      | 0     | 0.12    | 0.12 | 0.12  | 0.12  |
| **Nadir**   | 0      | 0     | 0.12    | 0.12 | 0.12  | 0.12  |
| **Forward** | 0.12   | 0.12  | 0       | 0    | 0.12  | 0.12  |
| **Aft**     | 0.12   | 0.12  | 0       | 0    | 0.12  | 0.12  |
| **North**   | 0.12   | 0.12  | 0.12    | 0.12 | 0     | 0     |
| **South**   | 0.12   | 0.12  | 0.12    | 0.12 | 0     | 0     |


</details>

## Acknowledgements

This material is based upon work supported by the National Science Foundation (NSF) Graduate Research Fellowship Program under Grant No. DGE-2039655. Any opinions, findings, conclusions, or recommendations expressed in this material are those of the author(s) and do not necessarily reflect the views of the NSF.

---

## How to Cite

TBD
