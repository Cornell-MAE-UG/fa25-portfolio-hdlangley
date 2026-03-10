---
layout: project
title: Heat Exchanger Thermodynamic Analysis
description: Class project with Graphs
technologies: [Heat Exchanger, Fluid Pump]
image: assets/images/Heat Exchanger.jpeg
---
**Collaborators:** Alyssa Schwartz, Emma Mukerji, Sofia Mykytenko, and Holbrook Langley


<h5>Experimental Design:</h5>
A heat exchanger is a device that facilitates heat transfer between the fluids without them mixing by flowing them in close proximity and allowing heat transfer across the internal physical barrier. In our experiment, the heat exchanger consisted of two pairs of inputs and outputs; each for different temperatures of liquid water as the working fluid. As they flow past each other in the heat exchanger, we predicted that the cold water should get warmer as heat moved from the hot source to the cold source. Similarly, we predicted that the hot water would get cooler as heat was lost to the cold flow. Both flows of water were fed into the heat exchanger by pumps with variable flow rates that we controlled by a setting on the pumps themselves ([VIVOSUN 210GPH Submersible Pump](https://vivosun.com/en-US/vivosun-130-210gph-submersible-pump500l-h-6w-or-800l-h-8w-ultra-quiet-water-pump-p68320123310965988-v58820960379607188)).

<div style="display:flex; gap:1rem; flex-wrap:wrap;">
  <figure style="flex:1; min-width:200px;">
    <img src="{{ '/assets/images/Pump Specifcations.jpg'| relative_url }}" alt="Image 1" style="width:100%; height:auto;">
    <figcaption>Pump specifications</figcaption>
  </figure>
  <figure style="flex:1; min-width:200px;">
    <img src="{{ 'assets/images/Pump.jpg' | relative_url }}" alt="Image 2" style="width:100%; height:auto;">
    <figcaption>Fluid Pump</figcaption>
  </figure>
</div>

We performed two trials of the experiment with the same starting temperature in the hot and cold reservoirs respectively. The heat exchanger remained in parallel flow for each trial, meaning the hot and cold flows were moving in the same direction through the heat exchanger control volume system. The flow rate of the pumps was set to the slow rate for the first trial (500 L/hr), and a fast rate for the second (800 L/H). In our model of the system, we assumed there is some heat transfer between the heat exchanger and the environment so the system is not adiabatic. We also assume that there is no change in kinetic and potential energy in the fluid throughout this experiment. 


<h5>System Diagram:</h5>
<div style="width:100%;">
  <img src="{{ '/assets/images/Heat Exchanger Diagram.png' | relative_url }}" alt="Heat exchanger system diagram" style="width:100%; height:auto; display:block;" />
</div>


<h5>Experimental Results:</h5>

<table>
  <thead>
    <tr style="background:#f0f0f0;">
      <th>Parameter</th>
      <th>Trial #1 Max Velocity (800 L/H)</th>
      <th>Trial #2 Min Velocity (500 L/H)</th>
    </tr>
  </thead>
  <tbody>
    <!-- Top 3 rows: red -->
    <tr style="background:#f8d7da;">
      <td><strong>Input Temp. of Hot Fluid (°C)</strong></td>
      <td>40</td>
      <td>40</td>
    </tr>
    <tr style="background:#f8d7da;">
      <td><strong>Output Temp. of Hot Fluid (°C)</strong></td>
      <td>23</td>
      <td>20.1</td>
    </tr>
    <tr style="background:#f8d7da;">
      <td><strong>ΔTemp. of Hot Fluid (°C)</strong></td>
      <td>17</td>
      <td>19.9</td>
    </tr>

    <!-- Next 3 rows: blue -->
    <tr style="background:#cfe2ff;">
      <td><strong>Input Temp. of Cold Fluid (°C)</strong></td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr style="background:#cfe2ff;">
      <td><strong>Output Temp. of Cold Fluid (°C)</strong></td>
      <td>19.8</td>
      <td>16.2</td>
    </tr>
    <tr style="background:#cfe2ff;">
      <td><strong>ΔTemp. of Cold Fluid (°C)</strong></td>
      <td>19.8</td>
      <td>16.2</td>
    </tr>

    <!-- Last row: purple -->
    <tr style="background:#e6d6ff;">
      <td><strong>ΔTemp. of Heat Exchanger (°C)</strong></td>
      <td>-7</td>
      <td>-2.5</td>
    </tr>
  </tbody>
</table>

<p style="font-size:0.9em; color:#444;"><em>*Both trials were performed in parallel flow through the heat exchanger</em></p>


<figure style="max-width:600px; margin:0 auto; text-align:center">
  <img src="{{ '/assets/images/Heat Exchanger Setup.jpg' | relative_url }}" alt="Short description" style="width:75%; height:75%; transform:rotate(270deg);">
  <figcaption>Heat Exchanger Flow Setup</figcaption>
</figure>

<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Heat Exchanger Balances</title>

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


<h5>Analysis:

<h6>Variable Definitions</h6>

$$

\begin{aligned}
T_{c,\text{in}} & : \text{Inlet temperature (cold)} \\
T_{c,\text{out}} & : \text{Outlet temperature (cold)} \\
T_{h,\text{in}} & : \text{Inlet temperature (hot)} \\
T_{h,\text{out}} & : \text{Outlet temperature (hot)} \\[6pt]
\dot{m}_h & : \text{Mass flow rate (hot)} \\
\dot{m}_c & : \text{Mass flow rate (cold)} \\
c_p & : \text{Specific heat of water}
\end{aligned}

$$


<h6>Mass Balance</h6>

$$\frac{dm_h}{dt} = 0 \quad \Rightarrow \quad \dot{m}_{h,\text{in}} = \dot{m}_{h,\text{out}}$$

$$\frac{dm_c}{dt} = 0 \quad \Rightarrow \quad \dot{m}_{c,\text{in}} = \dot{m}_{c,\text{out}}$$


<h6>Energy Balance</h6>
(assuming steady state, neglibale PE, KE and work flow rate)

$$\frac{dE_{cv}}{dt} = 0 = \dot{Q}_{cv} + \dot{m}_h c_p (T_{h,\text{in}} - T_{h,\text{out}}) + \dot{m}_c c_p (T_{c,\text{out}} - T_{c,\text{in}})$$

$$\dot{Q}_{cv} = \dot{m} c_p \left( (T_{h,\text{out}} + T_{c,\text{out}}) - (T_{c,\text{in}} + T_{h,\text{in}}) \right)$$



<h6>Entropy Balance</h6>

$$0 = \sum \dot{m}_{in} s_{in} - \sum \dot{m}_{out} s_{out} + \dot{S}_{gen} + \int \frac{dQ}{T_{b}}$$

$$

\dot{S}_{gen}
=
\dot{m}_h c_p \ln\!\left(\frac{T_{h,\text{out}}}{T_{h,\text{in}}}\right)
+
\dot{m}_c c_p \ln\!\left(\frac{T_{c,\text{out}}}{T_{c,\text{in}}}\right) - \int \frac{dQ}{T_{b}}

$$

$$

\dot{S}_{gen}
=
\dot{m} c_p \left(\ln\!\left(\frac{T_{h,\text{out}}}{T_{h,\text{in}}}\right)
+
 \ln\!\left(\frac{T_{c,\text{out}}}{T_{c,\text{in}}}\right)\right) - \int \frac{dQ}{T_{b}}
\ge 0

$$


<figure style="max-width:600px; margin:0 auto;">
  <img src="{{ '/assets/images/Real Heat Exchanger.jpg' | relative_url }}" alt="Short description" style="width:100%; height:auto;">
  <figcaption style="font-size:0.9em; color:#666; text-align:center;">Heat Exchanger Used</figcaption>
</figure>

<h5>How Slower Flow Rate Effects Efficiency:</h5>
The change we chose to investigate was changing the flow rate that the pump was moving water into the heat exchanger. Initially, we started with the same fast flow rate for each reservoir, and in the second round switched both the hot and cold reservoir pumps to the slower flow rate. 
Slowing the mass flow rate of both fluids altered the heat transfer between them. We believe the efficiency of the heat exchanger changed with time as the temperature difference between the two flows decreased with time. As the mass flow rate slowed, we expected there to be greater heat exchange between the two fluids. We observed this in the hot fluid but not the cold fluid. We believe this is because the heat exchanger started at a different initial temperature in the second trial (when the slower mass flow rate was used) because it had been affected by the initial experiment. Given enough time for the heat exchanger to reach room temperature again, we would expect both the cold and hot fluids to have a greater magnitude of temperature change from their initial conditions in the slow mass flow rate than in the hotter mass flow rate. Additionally, in our model, the heat exchanger is not an adiabatic system - some fraction of heat is lost to the environment via convection - which is why not all the heat from the hot fluid goes into the cold fluid for either trial. 

<p>

<figure style="max-width:600px; margin:0 auto; text-align:center">
  <img src="{{ '/assets/images/Group Selfie.jpg' | relative_url }}" alt="Short description" style="width:50%; height:50%;">
  <figcaption style="font-size:0.9em; color:#666; text-align:center;">Group Selfie!</figcaption>
</figure>