7# The Video Processing Project

# What is it?
This project was born from inspiration from seeing how quickly YouTube processes a user uploaded video.

### What problems are we looking at?
A conventional REST-Based server is facing several major problems when users attempt to upload videos:

  1. Interrupted uploads force users to restart the entire upload process, causing frustration, especially if they were close to completion.
  
  2. Large video files or too many requests can overwhelm the web server, leading to crashes or stalls until requests are fulfilled.
  
  3. During video processing, the server becomes unavailable for other requests, causing potential service disruptions.

### How do we solve this?
To solve the identified issues, the following decisions have been made:

  1. Decoupling Video Processing: Separate the video processing logic from the web servers' responsibilities. This ensures that the web servers        focus solely on serving and responding to HTTP requests, reducing their workload and improving overall performance.
  
  2. Implementing Exponential Backoff: To handle failed requests without overloading the servers, an exponential backoff mechanism is introduced.      This means that if a request fails, subsequent retries are made with progressively increasing time intervals between each retry attempt.          This prevents server overload during recovery from failed requests.
  
  3. Resumable Uploads: The architecture is being updated to support resumable uploads. This means allowing users to restart an interrupted upload from where it failed, rather than starting the entire upload process again. This feature enhances user experience and reduces frustration.

### Result
The proposed architecture addresses the major issues related to video uploads on the conventional REST-Based server:

  1. Users can now resume uploads from the point of interruption, saving time and effort in case of failures.

  2. The implementation of exponential backoff ensures that server overloads due to failed requests are minimized, enhancing overall system stability and performance.

  3. By separating video processing from the web servers, the servers can continue serving other requests even while processing video uploads, reducing service disruptions and enhancing scalability.

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
