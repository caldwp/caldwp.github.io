---
layout: page
title: Self-Balancing Segway
description: A self-balancing segway comprised of a single Lego NXT motor with wheels, and an Arduino MEGA with gyroscope and accelerometer sensors. The control system for this project was developed by linearizing non-linear differential equations, and using state feedback control realized using Simulink.
img: assets/img/mini_seg/mini_seg.png
importance: 2
category: academic
---

This project was part of my Mechtronics class at RPI, and taught us how to create linearized 
control systems for non-linear physical systems. The physics of a segway is non-linear, and this is
seen when separating the system into two parts - the wheel and the pendulum. Seen
below these diagrams were first analyzed with Newton's Laws, after which relationships were
developed between the resulting differential equations.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/mini_seg/fbd.png" title="free body diagrams" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

Using Matrix algebra, the non-linear state space equations were linearized, resulting in equations
for the linear and angular acceleration of the system. The resulting equations were then modeled in
Simulink with sensors for input and the motor voltage as output.

The control system is seen below, with the red circle indicating the block that the second screenshot 
was taken inside of.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/mini_seg/control_system.png" title="control system" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/mini_seg/function.png" title="states to voltage block" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

After flashing the control system to the Arduino, and ironing out any conversion or offset issues, 
the segway was able to balance for several hours and even come back from minor perturbation.
