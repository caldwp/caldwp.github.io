---
layout: page
title: Automated Home Server
description: My personal home server for gaming, cloud and media streaming applications with automated meta-data retrieval. Each service is containerized using Docker, and networking is done through NGINX Proxy Manager.
img: assets/img/home_server/server.jpg
importance: 1
category: home
---

This project stemmed from my desire to move my personal collection of movies, TV shows and music to 
a server that would allow me to access them from anywhere. Furthermore, it enabled me to make my own 
personal cloud storage for data privacy independent of Google, Microsoft or any other company. 
There are also smaller services running here, like automated meta-data and subtitles finders as 
well as some gaming services.

Hosting so many services can be problematic as it could result in the router being exposed to 
attacks on several ports. This is where containerization and having a reverse proxy come in 
handy. For starters, keeping applications "sandboxed" in containers makes it harder for potential
malware to spread about the system. Second, the presence of a reverse proxy allows all data to flow
through just a few ports. As seen in the image below, a reverse proxy redirects requests from clients
to different servers behind the router.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/home_server/proxy.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Visualization of a reverse proxy from <a href="https://learn.microsoft.com/en-us/previous-versions/windows/desktop/dd892097%28v=vs.85%29">Microsoft</a>.
</div>

This project has overall been a success and is one I am constantly working on, both for maintenance
and adding new features.
