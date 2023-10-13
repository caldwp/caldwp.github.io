---
layout: page
title: Wireless Audio Visualizer
description: An LED strip that receives audio data packets and creates a light show to match the audio environment in real time. Enabled by MQTT, NumPy and GPIO.
img: assets/img/aud_vis/aud_vis.png
redirect: #https://unsplash.com
importance: 3
category: academic
---

The goal of this project was to create a wireless device that used audio input to create matching light patterns. 
The motivation for this project came from the desire to have a room that effortlessly adapts its lighting to the local
audio environment. This primarily relates to musical applications, but can be used for any audio signal.

This project required a networking aspect as it was part of an IoT course, so it functioned with two devices 
communicating over MQTT. The data transmitter, which could be any device with internet access, took microphone input 
and output packets wirelessly to the receiver. The receiver, a Raspberry Pi attached to an individually addressable 
60 LED strip, then changed the brightness of each LED based on the volume of each frequency. The system diagram is 
shown below.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/aud_vis/diagram.png" title="high level system diagram" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    System Diagram
</div>

The first steps of the project were verifying that audio data could be acquired from the microphone, establishing a link 
between devices over MQTT, and verifying the LEDs could be properly set by the RPi over GPIO. After this was finished, 
the only task left was manipulating the data to be displayable on the LED strip.

Due to audio data being represented logarithmically as shown below in the figure on the left, averaging frequency bands 
wasn't as easy as linearlly dividing the frequency spectrum into 60 bands (# of LEDs) and averaging each one. This 
resulted in the formula in the figure in the middle being developed, which quickly averaged the data resulting in it's 
linear representation on the right. This calculation was quick using NumPy, and resulted in very little latency.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/aud_vis/log_data.png" title="audio data on a logarithmic scale" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/aud_vis/averager.png" title="conversion equation" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/aud_vis/lin_data.png" title="linearly represented data" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Audio Data Scale Conversion
</div>

The final demonstration of the project reacting live to music can be seen <a href="https://drive.google.com/file/d/1AeWkjft7KwteDXe5vmFd-4qaWfwHAn42/view?usp=sharing">here</a>.

Future improvements to this project would be to fix remaining latency issues, add an equalizer as certain frequencies have different brightness levels for the same volume, and test with multiple receivers of different LED strip sizes.
