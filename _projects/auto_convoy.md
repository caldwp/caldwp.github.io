---
layout: page
title: Autonomous Convoy
description: A multi-mobile robot system acting as a convoy of vehicles with the ability to diverge paths when needed. Built using OpenCV packages for ROS, stigmergy and the YAHBOOM ROSMASTER X3.
img: assets/img/auto_convoy/auto_convoy.png
importance: 1
category: academic
related_publications:
---

This project began as an experimentation with the autonomous driving package included with ROS on 
the YAHBOOM ROSMASTER X3 robot. While learning about OpenCV based applications in my Robotics II 
course, a teammate and I gained interest in autonomous mobile robots. This package uses the typical 
PID control for it's movement, and Hue Saturation and Value (HSV) control for color recognition. 
Pictured below, is a typical representation of HSV values. Saturation and value are typically 
represented as a number between 0 and 1, where hue is represented as a degree of rotation on the 
color wheel.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/auto_convoy/hsv.png" title="hsv" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
    </div>
</div>

Calibration was done with the user selecting an area on the camera output, which would cause the 
application to automatically define HSV values for the robot to follow. There were two initial 
causes of failure with this calibration. As seen in the middle image below, the robot mistook a 
white patch on the ground for the yellow tape and was taken off course. While this pointed to an 
issue in color differentiation by the program, an attempt was made to lower the robots linear 
speed as the sharp turn was almost completely missed and the yellow track was out of the robots 
field of view when it got off course. This resulted in the figure on the right, which showed the 
robots new found time was used for indecision, rather than a correct traversal of the path. This 
meant the HSV control definitely had to be recalibrated.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/auto_convoy/y_cal.png" title="initial color calibration" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/auto_convoy/fast_miss.png" title="initial miss" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/auto_convoy/color_miss.png" title="second miss" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

After directly changing the HSV values in the programs GUI, desireable results were not acheived, 
so calibration was redone from the start. This time the robot was place in front of both the white 
and yellow tape, which allowed for proper camera exposure adjustments and better color 
differentiation. This recalibration resulted in a successful completion of the course by the robot. 
During the course of the project, it was not discovered how to manually adjust the cameras 
exposure. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/auto_convoy/y_w_cal.png" title="color re-calibration" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
    </div>
</div>

The team was then tasked with creating a unique capability for the robot based on packages explored 
throughout the semester. Making an autonomous convoy seemed like a good next step. An early concept 
for this was to have the robots make a straightline formation and have a leader traverse the path. 
This idea was not pursued as mobile robot formations act as one rigid body, thus the straightline 
formation would only be acceptable on straightline paths. The idea the team chose to pursue was again 
based on HSV control, where the leader would be configured to follow yellow, and the follower would 
be configured to follow the color of the leaders light bar. In this case red was chosen, and 
modifications were made to the track to allow for path divergence as seen below.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/auto_convoy/track.png" title="track" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

The coordination of actors through their interactions with their environments is known as 'stigmergy'.
This is effectively how the robots would be convoying, as their light bar would color the environment
prompting action from following actors. Due to the problem with manually configuring camera exposure,
it was found to be more effective to calibrate the follower robot to the color of the light on the floor,
rather than the light bar itself which presented white on the camera.

<div class="row justify-content-sm-center">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/auto_convoy/r_cal.png" title="LED calibration" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/auto_convoy/auto_convoy.png" title="convoy" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

A successful convoy was made, albeit with some kinks to be worked out, and path divergence was also
a success. Demo seen <a href="https://photos.app.goo.gl/rokCXGskNyF79Bfq8">here</a>.
