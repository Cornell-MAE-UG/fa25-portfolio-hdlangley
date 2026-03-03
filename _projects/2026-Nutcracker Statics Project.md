---
layout: project
title: Nutcracker Statics Project
description: Class project to optimize the design of a nutcracker for Macedmica nuts
technologies: [Nut Cracker]
image: assets/images/nut-cracker-image.jpeg
---

<h5>Problem Statement and Objective:</h5>
The goal of this project is to create an effictive hand held design for a Macadamia Nuts. The main variable component of this design is the length of the handle which can be calculated. 

<h5>Constraints and Input Parameters:</h5>
The primary constraints are based on the force required to break a typical Macadamia Nut, its dimensions, and typical human grip strength. From these constraints the ideal handle length can be calculated.

<table>
  <thead>
    <tr>
      <th>Constraint</th>
      <th>Value</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Force required</td>
      <td>222 kg</td>
    </tr>
    <tr>
      <td>Grip Strength</td>
      <td>30 kg</td>
    </tr>
    <tr>
      <td>Nut Size</td>
      <td>2 cm</td>
    </tr>
  </tbody>
</table>

<h5>Problem Approach and Solution:</h5>
Starting off by making a free body diagram of the nutcracker reveals the applied forces and what equilibrium equation can be applied.

<div style="width:100%;">
  <img src="{{ '/assets/images/nutcracker-fbd.png' | relative_url }}" alt="Nutcracker free body diagram showing applied forces and moment arms labeled as L1, L2, Fa, and Fn around a hinge joint" style="width:100%; height:auto; display:block;" />
</div>

Using the sum of the moments about the origin (the joint of the nutcracker) the height and lenght ratio of the relevant triangles can be calculated.

<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Nutcracker Statics Project</title>

  <!-- MathJax -->
  <script src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>

  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 30px;
      line-height: 1.6;
    }
    h2 {
      margin-top: 40px;
    }
  </style>
</head>
<body>

$$\sum M_0 = L_2 \times F_a - L_1 \times F_n = 0$$

$$\frac{L_2}{L_1} = \frac{F_n}{F_a} = \frac{m_n}{m_a} = \frac{222 \text{ kg}}{30 \text{ kg}} = 7.4$$

Applying similiar triangles reveals the length required for the design.

$$\frac{L_2}{L_1} = \frac{H_2}{H_1} = 7.4 \Rightarrow H_2 = 7.4 H_1 \Rightarrow 7.4(2 \text{ cm}) = 14.8 \text{ cm}$$

Assuming the nutcracker holds the nut at an offset from the hinge at a distance of 4 cm, the length would be 29.6 cm.

$$\frac { L _ { 2 } } { L _ { 1 } } = 7.4 \Rightarrow 4 \text{ cm} ( 7.4 ) = L _ { 2 } = 29.6 \text{ cm}$$

<h5>Design Diagram:</h5>
<div style="width:100%;">
  <img src="{{ '/assets/images/nutcracker-diagram.png' | relative_url }}" alt="Nutcracker design diagram with dimensions showing handle length of 29.6 cm and nut position at 4 cm from hinge" style="width:100%; height:auto; display:block;" />
</div>

*Note: Diagram is not drawn to scale.*


<h5>Design Usability:</h5>
The calculated length of 29.6 cm is quite large for a nutcracker, especially one intended to be handheld. This length is nearly one foot, which would likely make it uncomfortable to hold and operate. In comparison, a typical smartphone designed to fit comfortably in the hand is about 16.5 cm long. The proposed nutcracker design would therefore be almost twice the length of an average smartphone.

Due to this large size, the applied force could instead be increased by incorporating a linear actuator. This modification would allow the design to be more compact and easier to use. However, it would also eliminate the possibility of the device being handheld.

<h8>Sources:</h8>
https://www.coolblue.be/en/advice/smartphone-screens.html
https://www.dexdia.com/blog/printable-grip-strength-norms?srsltid=AfmBOopGyJ4lwKpdszk2zZcXalr49JAjAtzmAt3O33tWswmH5HDN_VLt
https://doi.org/10.1007/s10071-007-0131-2
https://alohafarmshawaii.com/services/macadamia-nuts/#:~:text=Macadamia%20Nuts%20are%20described%20as,50%25%20whole%20kernel%20by%20weight.

</body>
</html>