# Elephant Foodbank ModelBuilder

## Overview

This repository provides the ArcGIS ModelBuilder toolbox developed for the identification of potential elephant food bank sites in Johor, Peninsular Malaysia.

The toolbox implements a spatial multi-criteria decision analysis (MCDA) framework by integrating ecological suitability, elephant movement ecology, human–elephant conflict (HEC), riparian habitat, and interaction risk into a single spatial decision-support workflow.

This repository was developed to improve the transparency and reproducibility of the modelling framework described in the associated publication.

---

# Repository Contents

```
Elephant-Foodbank-ModelBuilder
│
├── Elephant Foodbank Modeller.tbx
├── README.md
├── LICENSE
└── (Optional)
    ├── User_Guide.pdf
    └── Workflow.png
```

---

# Software Requirements

The toolbox was developed using:

- ArcGIS Desktop / ArcGIS Pro
- ModelBuilder
- Spatial Analyst Extension

---

# Workflow Overview

The toolbox integrates six spatial submodels before producing the final food bank suitability map.

```
Habitat Suitability
          │
Interaction Risk
          │
Riparian Habitat
          │
HEC Hotspots
          │
Movement Density
          │
Home Ranges
          │
      Factor Overlay
          │
 Potential Elephant
 Food Bank Sites
```

---

# Required Input Layers

The toolbox requires six processed spatial layers generated from previous modelling procedures.

## 1. Elephant Habitat Suitability

Source:
- MaxEnt habitat suitability model

Processing:

- Habitat suitability map classified into suitability classes.
- High suitability areas extracted.
- 1 km buffer generated.

Purpose:

Identify ecologically suitable habitat for elephants.

---

## 2. Human–Elephant Interaction Risk

Source:

- MaxEnt interaction risk model

Processing:

- High interaction risk areas extracted.
- Buffered by 10 km.

Purpose:

Avoid locating food banks in areas with high potential human–elephant interaction.

---

## 3. Riparian Habitat

Source:

- Water bodies

Processing:

- Water bodies within elephant range forest blocks or within 10 km of forest blocks retained.
- Buffered by 1 km.

Purpose:

Represent important water resources and riparian habitats used by elephants.

---

## 4. Human–Elephant Conflict (HEC) Hotspots

Source:

- Kernel Density Estimation (KDE)

Processing:

- KDE classified.
- Moderate and High conflict classes extracted.
- Buffered by 5 km.

Purpose:

Identify conflict-prone areas where food bank intervention may reduce elephant pressure.

---

## 5. Elephant Movement Density

Source:

- GPS collar locations

Processing:

- GPS fixes converted to movement trajectories.
- Line Density Analysis performed.
- Forest-edge movement analysed within a 200 m boundary buffer
  (100 m inside and 100 m outside forest edge).
- High movement density retained.

Purpose:

Identify major elephant travel corridors and movement routes.

---

## 6. Elephant Home Ranges

Source:

- GPS collar data

Processing:

- Individual 95% Fixed Kernel home ranges generated.
- Individual home ranges merged into a composite layer.

Purpose:

Represent areas regularly occupied by collared elephants.

---

# Factor Overlay

The six processed spatial layers are integrated using overlay analysis within ArcGIS ModelBuilder.

The overlay identifies locations where:

- Suitable elephant habitat occurs;
- Elephant movement is concentrated;
- Home ranges overlap;
- Water resources are accessible;
- Human–elephant conflict mitigation is required; and
- Areas with high interaction risk are appropriately screened.

The final output represents potential elephant food bank locations.

---

# Model Output

The toolbox produces:

- Potential elephant food bank suitability map
- Candidate food bank locations
- Intermediate overlay layers (optional)

---

# Data Availability

The original datasets used in this study are **not included** in this repository because they contain sensitive wildlife information, including GPS locations of Asian elephants and human–elephant conflict records.

Users may apply their own datasets following the workflow implemented in this toolbox.

---

# Limitations

The toolbox does not automatically generate habitat suitability, interaction risk, movement density, home ranges, or HEC hotspot layers.

These layers must be prepared prior to running the toolbox.

The quality of the final output depends on the quality and spatial resolution of the input datasets.

---

# Citation

If this toolbox contributes to your research, please cite the associated publication:

> **(To be updated after publication.)**

---

# Contact

**Developer**

Amirul Hakimi

Faculty of Applied Sciences

Universiti Teknologi MARA (UiTM)

Malaysia

For questions regarding the toolbox, please contact the repository owner through GitHub.
