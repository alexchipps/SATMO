# SATMO

**Spacecraft Albedo & Thermal Model (SATMO)**

SATMO is a lightweight MATLAB-based thermal analysis tool designed to simulate the thermal environment of a small spherical spacecraft orbiting Earth. The model estimates absorbed radiation from three key sources:

* Direct solar radiation
* Earth albedo
* Earth infrared (IR) emission

This repository is an academic and research-oriented resource for quick‑turn thermal modeling, particularly useful for conceptual spacecraft design, student research, early‑phase thermal studies, and educational demonstrations.

---

## 🚀 Key Features

* One‑node thermal model of orbiting spacecraft
* Incorporates view factors for Earth albedo & IR
* MATLAB implementation with adjustable orbital parameters
* Consistent radiative flux handling (solar, albedo, and planetary IR)
* Reference formulas for rapid spacecraft thermal budget evaluation

---

## 📂 Repository Structure

```
SATMO/
├── src/               # MATLAB scripts and core model functions
├── docs/              # Supplemental technical notes and references
├── examples/          # Example configurations and plots
└── README.md
```

---

## 🧠 Background

This model is based on classical spacecraft thermal theory, using cross‑sectional area absorption for direct solar load and spherical view factors for diffuse Earth albedo and IR loads.

The governing energy balance is:
$$
Q_{in} - Q_{out} = m c_p \frac{dT}{dt}
$$

Where inputs include:

* Solar constant
* Planetary albedo
* Planetary IR emission
* Emissivity/absorptivity
* Orbit geometry

---

## ✅ Usage

Clone the repo and run the main MATLAB script:

```matlab
run('satmo_main.m')
```

Adjust spacecraft and orbit parameters inside the configuration block.

---

## 📎 References

A set of academic and aerospace references are included in the `docs/` folder, including view factor derivations and standard spacecraft thermal constants.

---

## 🛠 Future Plans

* Multi‑node expansion
* Better orbital propagator
* Non‑spherical geometry support
* GUI front‑end (MATLAB App Designer)

---


## 📜 License

MIT License

---

## ✨ Acknowledgements

Developed as part of independent spacecraft thermal modeling research. Special thanks to open aerospace communities and academic contributors.

---

## 👨‍🚀 Maintainer

**SATMO Developer**

If you'd like to explore spacecraft thermal topics or collaborate, feel free to reach out!
