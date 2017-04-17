---
layout: page
title: Blynk Library demo
permalink: /Courses/blynk-library/
---

# Blynk Server

1. Download the Blynk application on your smartphone.

2. Get the raspberry pi updated and ready
  - Install Raspian
  - sudo apt-get update
  - sudo apt-get upgrade

3. Power up the pi and connect it to the internet

4. Connect a few gpio pins to the positive lead of your lead and connect the ground to the ground pin on the pi

![Rapsberry Pi Pinout]()

5. Open up blynk and add a button
  - Select the appropriate gpio pin associated to the led

6. Install blynk-library on the pi
  - Link is https://github.com/blynkkk/blynk-library/tree/master/linux

7. Clone the git repo through the code ```git clone https://github.com/blynkk/blynk-library.git```

- Run ```cd blynk-library/linux```
- Run ```make clean all target=raspberry```

8. To run blynk, us the code ```sudo ./blynk --token=YourAuthToken```
