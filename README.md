# Urban-Noise-Sim
A simplified urban noise simulation template using Rhino 3D and Grasshopper to assist in early-stage architectural or landscape design.

![image](https://github.com/differential-studio/Urban-Noise-Sim/blob/main/251224_GitHub%20Animation_5.gif) 

In an era of rapid urbanization and increasing density, understanding acoustic comfort has become crucial for livable city design. Noise pollution, traffic proximity, and inadequate zoning pose risks to public health and resident well-being. Moreover, proper facade orientation and massing are essential for interior acoustic quality. Early-stage noise exposure analysis can help identify potential problem areas before they manifest, leading to more informed design decisions and healthier built environments.

This Grasshopper script provides architects, urban planners, and designers an accessible tool for analyzing potential urban noise impact on building geometries. By visualizing and understanding approximate noise propagation in landscape, urban, and architectural contexts, designers can make more informed decisions about site planning, massing strategies, and mitigation requirements.

## Overview
This tool uses a simplified geometric ray-casting model to simulate noise propagation from road networks, providing indicative visualization of:

- Direct noise exposure
- Relative noise intensity on building facades
- Impact of road hierarchy (lane count) on noise levels
- Distance-based sound attenuation

## Features
### Noise Source Simulation
The script simulates sound emission using mesh spheres distributed along road centerlines. The process works as follows:
- Emitters: Mesh spheres are generated at regular intervals along roads
- Ray-Casting: Vectors are "shot" from the center of every face of these spheres, simulating omnidirectional sound waves
- Intersection: The script calculates where these vectors hit the surrounding context geometry

### Intensity Calculation
The tool calculates a predicted noise value for every hit point on the context mesh based on:
- Distance: The length of the ray from the source sphere to the building facade
- Source Intensity: The type of road the sphere originated from (defined by the number of lanes)
The result is a colored mesh (heatmap) showing relative noise exposure levels, allowing users to:
- Identify facades with critical noise exposure
- Compare different massing options for acoustic shielding
- Visualize the impact of widening roads or changing traffic patterns

Noise values used in the script were referenced from this study: https://www.researchgate.net/publication/228381219_The_Effects_of_Highway_Noise_on_Birds

### Parameters
- ```Model units```: Ensures proper scaling of the analysis
- ```Number of rays```: Determines number of rays from one noise source
- ```Distance between noise sources```: Determines the distance between points that emits noise
- ```Grid size```: Determines the resolution of the output analysis mesh
- ```Average result```: Averages the noise value on each analysis mesh face (especially useful when the "Number of rays" value is low)

## Implementation
The tool consists of two main parts:
1. Ray-Casting leveraging:
  - MeshRay intersections
  - Functionalities for calculating distance-based attenuation
2. Visualization implemented through Grasshopper components:
  - Coloring mesh faces based on accumulated hit values
  - Legend generation
  - Data normalization for visual clarity

This dual implementation approach makes the tool both powerful and easily customizable within the familiar Grasshopper environment.

## Limitations and Disclaimer
This tool is intended for preliminary analysis and visualization purposes only. It should not be used as the sole basis for critical design decisions or engineering calculations. The simulation does NOT account for:
- Sound reflection (echo)
- Sound diffraction (bending around corners).
- Frequency-specific analysis (Hz).
- Material absorption properties (e.g., glass vs. concrete).
- Atmospheric conditions (wind, temperature, humidity).
- Topography effects (unless modeled in the mesh).
- Real traffic flow dynamics (speed, stop-and-go).
- Background noise or non-traffic sources.
- Local decibel (dB) regulations.

## Intended Use
This tool is best used for:
- Early-stage massing analysis
- Comparing relative noise exposure between massing options
- Visualizing the "acoustic shadow" cast by buildings
- Educational purposes 
- Communication with stakeholders about zoning
- Identifying facades that may require higher STC (Sound Transmission Class) ratings.

## Requirements
- Rhinoceros 3D (version 8)
- Grasshopper
- GHPython
- Grasshopper Plugin: Bifocals 
- Grasshopper Plugin: ARMy Ant
- Grasshopper Plugin: eleFront

## License
This project is licensed under the MIT License - see the LICENSE file for details. This means you can freely use, modify, and distribute this tool, but please provide attribution to the original authors.

## Contributing
We welcome contributions to improve the script! If you encounter any issues or have suggestions for enhancements, please feel free to contact us at hello@differential.works.
