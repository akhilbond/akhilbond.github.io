---
layout: page
title: ROS
permalink: /Courses/ROS/
mathjax: true
---

# <u>ROS(Robot Operating System)</u>

1. Go to the [www.ros.org](www.ros.org)
2. Go to the install page under the Getting Started option
3. Select the desired version of ROS for your computer(For this tutorial, I will be installing ROS Indigo Igloo for Ubuntu Linux)
4. Click install and you will be redirected to the wiki of the ROS build
5. Follow the steps of the ROS wiki page

- First run the code below to accept software from packages.ros.org

```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```

- Next run the code to setup keys for the build

```
sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net --recv-key 421C365BD9FF1F717815A3895523BAEEB01FA116
```

- Run the following command to make sure that your Debian package index is up to date
```
sudo apt-get update
```

- For the desktop full install, run the following ```
sudo apt-get install ros-indigo-desktop-full
```
