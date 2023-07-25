# The Video Processing Project

# What is it?
This project was born from inspiration from seeing how quickly YouTube processes a user uploaded video. In order to mimic some of that functionality this project was born.

### What problems are we looking at?
When a user attempted to upload a video to a conventional REST-Based server, they are met with a few major problems:
  1. If an upload is intterupted, users will have to restart the entire upload. This can be punishing if they're at 98% and no safeguards are in place.
  2. If too many requests are made or the video files are too large the web server can crash or stall until the request is fufilled.
  3. While processing, no other requests can be made.

### How do we solve this?
How we solve this issue will determines how our architecture will look like. These are the decisions I've decided on:
  1. Separate the video processing logic away from the web servers as they should only be concerned about serving and responding to HTTP requests.
  2. Implement exponential backoff for requests that fail so that servers are not overloaded whilst trying to recover the failed requests.
  3. (In progress) Allow a user to restart an upload where it failed.

With this in mind I've designed this architecture
![image](https://github.com/MarkRivera/video-processing/assets/6520868/62677026-d995-4330-aa1f-81245fe2e3b2)

# Major Components
There are 4+ major components to this application:
  1. Client Application
  2. Web Servers
  3. RabbitMQ Task Queue
  4. Golang Workers


## Client
  ### **Tech Stack**
  
  TypeScript, React, Vite, Docker, Tailwind, Jest
