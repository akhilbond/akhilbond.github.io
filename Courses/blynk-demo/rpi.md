---
layout: page
title: Blynk Library demo
permalink: /Courses/blynk-demo/
---

<br>

This is a demo of the [blynk server](http://www.blynk.cc/) in conjunction with the Raspberry Pi 3 Model B. The steps to setup wireless LEDs are below.

<br>

1. Download the Blynk application on your smartphone.
- You should create an account using your email or facebook.<br><br>

2. Create a project in the Blynk app.

- Add a project name or your choosing.
- Choose **Raspberry Pi 3 B** as the device.
- **MAKE SURE TO SAVE THE EMAIL WITH THE AUTH TOKEN FOR THE PROJECT**

3. Get the raspberry pi updated and ready
  - Install Raspian on the sd card for the pi
  - Run ```sudo apt-get update``` to retrieve the most recent linux packages
  - After that, run ```sudo apt-get upgrade``` to install the linux package updates

4. Power up the Pi using a micro usb cable and connect it to Wi-Fi.

5.  Select a few gpio pins to use on the pi and connect jumper cables to them. Also add a jumper cable to the ground gpio pin

![Rapsberry Pi Pinout]()

6. Connect the gpio jumper cables to the positive lead of the led(long pin).
- Connect the ground jumper cable to the ground bar of the bread board.
- Connect the negative lead of the led(short pin) to the ground.

7. Open up Blynk and add a button, per led on the breadboard, to the project you created

8. Select the appropriate gpio pin associated to the led of the button

9. The github repo with the Blynk server code is located at the link below.
  - https://github.com/blynkkk/blynk-library/tree/master/linux

10. Clone the git repo through the code ```git clone https://github.com/blynkk/blynk-library.git``` to download the blynk server code.

11. Run ```cd blynk-library/linux``` to move to the *linux* subdirectory in the *blynk-library*

12. Run ```make clean all target=raspberry``` to clean unnecessary files and configure the server codes to the raspberry pi

13. To run the Blynk server on the pi, run the command ```sudo ./blynk --token=YourAuthToken```. Replace *YourAuthToken* with the auth token located in the email when you created the Blynk project in the app

14. Click the play button in the top right corner of the Blynk app, and then press a button to have the leds turn on from the Pi.
