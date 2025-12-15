---
layout: project
title: Instrumented Torque Wrench
description: "600 in-lbf rated Instrumated Torque Wrench"
technologies: [SolidWorks, Ansys]
#image: /assets/images/spaceship-design.jpg
---

## [Assignment Description]
I was assigned to design a non-ratcheting, 3/8 inch drive instrumented torque wrench
rated for 600 in-lbf.

The torque will be transduced by strain gauges on the sides of the torque wrench. The
design goal is to maximize the voltage output of the wrench (mV/V) at the rated torque.
The design is required to attain at least 1.0 mV/V output at the rated torque of 600 in-
lbf. Higher output will lead to more sensitivity and improved signal to noise ratio. The
constraints are that the wrench must not fail due to static loading, crack growth or fatigue.

The wrench must sustain a fully reversed torque of
T = ±600 in-lbf for 106 cycles. 
Design will include selecting an appropriate material and dimensions to meet or exceed the following requirements:
• attain at least 1.0 mV/V output at the rated torque of 600 in-lbf.
• safety factor of Xo = 4 for yield or brittle failure
• safety factor of XK = 2 for crack growth from an assumed crack of depth 0.04 inches (1 mm).
• fatigue stress safety factor of XS = 1.5.
• material must be a steel, aluminum or titanium alloy.

## [Basic Design and Hand Calculations.]

### [Material Selection]

The wrench will be one solid body, to avoid bonding weaknesses. Therefore there will be one material selected for the core part of the wrench. There are a few material properties that are relevant in the determination of the material used for the wrench. The tensile strength is what determines the safety factor against non-brittle failure. The material should not be brittle, because the wrench should have a considerable elastic regime in which the strain gauge section can deform. This will increase the sensitivity of the instrumentation device. It is also very important that the material has a high fracture toughness. This is because in order to increase the sensitivity of the wrench the cross section at the strain gauge needs to be reduced, which can reduce the factor of safety against crack growth. Aluminium has far lower strength and toughness than steel and titanium.
The comparison in the chart it becomes clear that while M-Series tooling steels (like M42) have a higher young’s modulus they have comparatively lower fracture toughness. High Alloy Steels have a very high fracture toughness and are less strong than some Tooling Steels and other alloy steels. High Alloy Steel AF1410 was chosen due to its relatively high yield strength, fracture toughness, and Young's modulus.

![Yield Strength vs Fracture Toughness for a Variety of Steel, Aluminium, and Titanium Alloys]({{"assets\images\InstrumatedTorqueWrench\PropertyGraph.png" | relative_url }}){: .inline-image-l}

**High Alloy Steel AF1410**:
- Young's Modulus: *29.4 E6 psi*
- Poissons Ratio: *0.3*
- Yield Strength (Elastic Limit): *215 ksi*
- Fatigue Strength: *94.3 ksi*
- Fracture Toughness: *137 ksi √in*


The wrench was designed to withstand a maximum applied torque of 1200 in-lbf or 100 ft-lbf which is within a reasonable range for high torque manual wrenches. The strain gauge uses a full wheatstone bridge to maximize the instrumentation output. A full Wheatstone bridge is twice as sensitive as a half-bridge because it uses four active strain gauges (two in tension, two in compression). Here are the basic dimensions of the wrench.

- L = *16"*
- h = *0.65"*
- b = *0.45"*
- c = *1"*

This design and material selection resulted in the following design outcomes.

- Maximum Normal Stress: 37.8698 ksi
- Deflection: 0.33821 in

- Safety Factor for Strength: 18.93
- Safety Factor for crack growth: 18.2236
- Safety Factor for fatigue: 4.9802
 

- Strain at gauge: 603.7918 microstrain
- mV per V at 600 lb-in using full bridge: 1.2076

With the analytical results of the baseline design showing promising results I moved on the final CAD design.

### CAD Model

![Full CAD Model of Final Design]({{"assets\images\InstrumatedTorqueWrench\FullCAD.png" | relative_url }})

The CAD model is primarily based on the basic dimensions from the hand calculation. The width is reduced to 85% of the nominal width of the wrench “h”. The ends of the wrench are circular. And the width of the wrench linearly varies between ends and the strain gauge section. Edges were filleted to reduce stress concentrations wherever possible. ⅜” drive with 0.1” filleted edges.


![Basic Dimensions of Wrench]({{"assets\images\InstrumatedTorqueWrench\Drawing.png" | relative_url }}){: .inline-image-1}


### FEM Analysis

#### Boundary Conditions

The Boundary Conditions were set so that there was zero displacement at the drive. Similar to a fixed support. And at grip edge of the wrench a force of 37.5 lbf was applied, corresponding to the 600 lbf-in loading condition specificed in the requirements.

![Zero Displacement Boundary Condition]({{"assets\images\InstrumatedTorqueWrench\BoundaryConditions.png" | relative_url }})

![Force BoundaryCondition]({{"assets\images\InstrumatedTorqueWrench\ForceCondition.png" | relative_url }})

#### FEM Solution

The first solution shows that the reduction in handle thickness at the strain gauge location is effective in increase location strain. The strain probe placed reveals a maximum strain of 1016 microstrain which is around 66% greater than the rectangular design.

![Maximum Normal Strain in Gauge Direction]({{"assets\images\InstrumatedTorqueWrench\MaxStrain_Close.png" | relative_url }})

![Strain Gauge Location]({{"assets\images\InstrumatedTorqueWrench\MaxStrain_Close_Probe.png" | relative_url }})

While the stress at the handle bar surface is around the predict 20 ksi range the stress at the base of the drive far exceeds the predicted maximum normal stress. 95.547 ksi at the locations stress concentration.

![Maximum Stress]({{"assets\images\InstrumatedTorqueWrench\MaxStress_Close.png" | relative_url }})

The of 0.2626" deflection also exceeds the analytical value of 0.1691"

![Deflection of Wrench]({{"assets\images\InstrumatedTorqueWrench\Deflection.png" | relative_url }})

After running a convergence study at the areas of high stress concentration and the strain gauge location these were the final values of interest under the 600 lbf-in loading.

![Refinement  Location]({{"assets\images\InstrumatedTorqueWrench\Refinement.png" | relative_url }})

The new maximum strain at the gauge location is 1232 microstrain, indicated even greater sensitivity than had been expected.

![Maximum Normal Strain in Gauge Direction - Post Refinement]({{"assets\images\InstrumatedTorqueWrench\MaxStrain_Close_Refinement.png" | relative_url }})

The stress concentrations have become more localized and exacerbated reaching values as high as 186 ksi. These are in very localized areas however, and should not lead to yielding.

![Maximum Normal Stress - Post Refinement]({{"assets\images\InstrumatedTorqueWrench\MaxStress_Close_Refinement.png" | relative_url }})

#### Strain Gauge
Strain Gauge Type: *SgT-2/1000-FB41*
FULL WHEATSTONE BRIDGE STRAIN GA
Manufacturer: *Omega*
Supplier: *Digikey*
Dimensions: *0.315” x 0.256” (carrier)*
Dimensions: *0.071” x 0.094” (grid)*
Solder Pad Termination
VRMS:*12*
Temperature compensation: *Steel*

![Strain Gauge Trace]({{"assets\images\InstrumatedTorqueWrench\StrainGauge.png" | relative_url }}){: .inline-image-1}

![Strain Gauge CAD]({{"assets\images\InstrumatedTorqueWrench\StrainGaugeCAD.png" | relative_url }}){: .inline-image-1}
