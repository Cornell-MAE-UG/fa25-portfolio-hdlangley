---
layout: project
title: "Nutcracker Linear Actuator"
description: Nutcracker linear actuator design and beam deflection analysis
technologies: [Nutcracker, Beam bending, Linear actuator]
image: assets/images/Nutcrakcer Linear actuator cover image.jpeg
author: Holbrook Langley
---

# Nutcracker Linear Actuator

##### Problem Statement and Objective

The goal of this project is to design a compact, mass-efficient nutcracker for Macadamia nuts. In the original rigid-body design, the required handle length of 29.6 cm was found to be impractically large for a handheld device, so a linear actuator is incorporated to allow a more compact form. This second phase of the design treats the handles as flexible beams and selects a cross-section that limits elastic deflection while minimizing mass.

##### Constraints and Input Parameters

| Constraint | Value |
| --- | --- |
| Force required to crack nut | 222 kg (≈ 2177 N) |
| Actuator grip force | 30 kg (≈ 294 N) |
| Nut diameter | 2 cm |
| Nut contact distance from hinge (a) | 4 cm |
| Handle length (L) | 29.6 cm |
| Maximum allowable deflection | 2% of handle length |

##### Beam Model and Assumptions

The handle is modeled as a **simply supported beam** (Appendix E, Case 5):

- The hinge joint near the nut acts as a **pin support** at end A.
- The linear actuator attachment point acts as a **roller support** at end B.
- The nut reaction force $P = 2177$ N acts as a **point load** at distance $a = 4$ cm from A.
- Only the transverse component of forces is considered.
- Small deflections and linear elastic behaviour are assumed.
- The beam cross-section is uniform along its length.

![Nutcracker free body diagram]({{ '/assets/images/Nutcracker FBD.png' | relative_url }})

##### Material and Cross-Section Selection

The design objective is to minimise mass subject to the stiffness constraint. For a beam under a deflection limit, the relevant material efficiency index is:

$$\frac{\rho}{E^{1/2}}$$

A lower value means less mass for the same stiffness. Comparing available materials:

| Material | Density ρ (kg/m³) | Modulus E (GPa) | ρ / √E |
| --- | --- | --- | --- |
| Structural steel | 7860 | 200 | 556 |
| **Aluminum** | **2710** | **70** | **324** |
| Brass | 8470 | 105 | 827 |
| Bronze | 8800 | 95 | 903 |
| Titanium | 4730 | 115 | 441 |

**Aluminum** has the lowest index and is therefore the most mass-efficient choice.

A **solid circular cross-section** is used for simplicity of manufacture and symmetric bending resistance. The relevant material properties are:

| Property | Value |
| --- | --- |
| Density ρ | 2710 kg/m³ |
| Modulus of Elasticity E | 70 GPa |
| Yield Strength (tension) σ_y | 95 MPa |
| Yield Strength (shear) τ_y | 55 MPa |

##### Part (a) — Location of Maximum Deflection

Using the Case 5 simply supported beam formula (Appendix E), with $a = 0.04$ m and $b = L - a = 0.256$ m:

$$x_m = \sqrt{\frac{L^2 - b^2}{3}}$$

$$x_m = \sqrt{\frac{(0.296)^2 - (0.256)^2}{3}} = \sqrt{\frac{0.02208}{3}} = \sqrt{0.007360} = 0.0858 \text{ m}$$

**The maximum deflection occurs at $x_m = 8.58$ cm from the hinge**, which lies between the nut contact point and the midspan. This makes physical sense: the load is applied very close to the pin support, so the beam bows most on the longer unsupported span.

The support reactions are:

$$R_A = \frac{Pb}{L} = \frac{2177 \times 0.256}{0.296} = 1883 \text{ N}$$

$$R_B = \frac{Pa}{L} = \frac{2177 \times 0.04}{0.296} = 294 \text{ N}$$

The maximum bending moment occurs at the load point $x = a$:

$$M_{max} = R_A \cdot a = 1883 \times 0.04 = 75.3 \text{ N·m}$$

##### Part (b) — Cross-Section Sizing

The maximum deflection from Case 5 (Appendix E) is:

$$\delta_{max} = \frac{Pb(L^2 - b^2)^{3/2}}{9\sqrt{3} \cdot E \cdot I \cdot L}$$

Setting $\delta_{max} \leq 2\%$ of $L$:

$$\delta_{limit} = 0.02 \times 0.296 = 0.00592 \text{ m}$$

Rearranging for the required second moment of area:

$$I_{min} = \frac{Pb(L^2 - b^2)^{3/2}}{9\sqrt{3} \cdot E \cdot \delta_{limit} \cdot L}$$

Computing the numerator:

$$(L^2 - b^2) = (0.296)^2 - (0.256)^2 = 0.02208 \text{ m}^2$$

$$(0.02208)^{3/2} = 0.02208 \times \sqrt{0.02208} = 0.02208 \times 0.14860 = 3.281 \times 10^{-3} \text{ m}^3$$

$$\text{Numerator} = 2177 \times 0.256 \times 3.281 \times 10^{-3} = 1.828 \text{ N·m}^3$$

Computing the denominator:

$$9\sqrt{3} \times 70 \times 10^9 \times 0.00592 \times 0.296 = 1.132 \times 10^9$$

Therefore:

$$I_{min} = \frac{1.828}{1.132 \times 10^9} = 1.615 \times 10^{-9} \text{ m}^4$$

For a solid circular cross-section, $I = \dfrac{\pi d^4}{64}$, so:

$$d_{min} = \left(\frac{64 \cdot I_{min}}{\pi}\right)^{1/4} = \left(\frac{64 \times 1.615 \times 10^{-9}}{\pi}\right)^{1/4} = 0.01345 \text{ m}$$

Rounding up to the next whole millimetre:

$$\boxed{d = 14 \text{ mm, solid aluminum rod}}$$

**Verification:**

$$I = \frac{\pi (0.014)^4}{64} = 1.886 \times 10^{-9} \text{ m}^4$$

$$\delta_{max} = \frac{1.828}{9\sqrt{3} \times 70 \times 10^9 \times 1.886 \times 10^{-9} \times 0.296} = \frac{1.828}{3.562} = 0.00513 \text{ m} = 1.73\% \text{ of } L \checkmark$$

**Mass comparison** showing the benefit of aluminum over steel:

| Material | Diameter | Mass per handle |
| --- | --- | --- |
| Structural steel | 10 mm | 18.3 g |
| **Aluminum (chosen)** | **14 mm** | **12.3 g** |

Despite the larger diameter, the aluminum rod is **33% lighter** than the equivalent steel design.

##### Part (c) — Final Design

![Nutcracker design diagram]({{ '/assets/images/Nutcracker Design.png' | relative_url }})

The final handle design is a **14 mm diameter solid aluminum rod**, 29.6 cm long. The linear actuator is mounted at the far end (roller support), and the nut sits 4 cm from the hinge pin. The maximum elastic deflection under full load is 5.13 mm, which is 1.73% of the handle length — within the 2% allowance.

The selected actuator is the **Progressive Automations PA-14P** (450 lb / ~2000 N rated force). The required actuator force is only 294 N, well within the rated capacity, providing a comfortable safety margin.

| Design parameter | Value |
| --- | --- |
| Material | Aluminum |
| Cross-section | Solid circle |
| Diameter | 14 mm |
| Length | 29.6 cm |
| Second moment of area I | 1.886 × 10⁻⁹ m⁴ |
| Max deflection | 5.13 mm (1.73% of L) |
| Mass per handle | ~12.3 g |
| Linear actuator | Progressive Automations PA-14P |

##### Usability

The 14 mm aluminum rod keeps the device compact and lightweight. The incorporation of a linear actuator eliminates the need for a long handheld lever, resolving the original impracticality of the 29.6 cm rigid design. The trade-off is that the device is no longer fully handheld — it requires a power source for the actuator — but it is far more compact and requires no manual grip strength.

##### Sources

- [Smartphone screen size reference](https://www.coolblue.be/en/advice/smartphone-screens.html)
- [Grip strength norms](https://www.dexdia.com/blog/printable-grip-strength-norms)
- [Macadamia nut hardness study](https://doi.org/10.1007/s10071-007-0131-2)
- [Macadamia nut properties](https://alohafarmshawaii.com/services/macadamia-nuts/)
- [Progressive Automations linear actuators](https://www.progressiveautomations.com/collections/linear-actuators)

**Technologies Used**: Beam bending analysis, Appendix E Case 5 deflection formula, material efficiency index