---
date: 2025-2-15 12:26:40
layout: post
title: "Robotics"
subtitle: "A Robotics & Programming Journey"
description: "A Robotics & Programming Journey"
image: /assets/img/alpha.png
optimized_image: /assets/img/alpha.png
category: Robotics
tags:
  - Robotics
  - Programming
  - Project

author: Jia Lim
---
<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>


<h3 class="toc_title">Project</h3>

My first big project was programming a VEX robot to autonomously drive through a maze — no human control, just pure code. I wrote a driving function called JiasdrivingCode() that told the robot exactly how far to drive forward and when to turn left or right, using a series of driveFor and turnFor commands measured in inches and degrees. The robot also had a lift mechanism controlled by amlift.spinFor, which helped it interact with elements along the course.
Alongside the driving code, my teammate Manushri designed a screen display for the robot's brain — a red rectangle with a diagonal line and a cheerful "hi there!! <3" message printed on screen. It was a fun way to give our robot some personality while it navigated!


<h4 class="toc_title">Step 1: 3 Themes Screen Design</h4>


This was one of my favorite challenges — designing three completely different animated scenes to display on the VEX Brain's small screen. Each theme had its own visual style and animation logic.

🌃 Starry Night
The starry night scene draws a black background, a crescent moon made from two overlapping yellow and black circles, and a field of white star dots scattered across the sky. On top of that, I animated a shooting star that moves across the screen from left to right, leaving a yellow trail behind it using the nightsky() function with a while loop.

🚕 Car Design
The car scene features an orange car driving across a blue sky and black road. The car body is built from three overlapping rectangles and two circles for wheels, and the whole thing moves horizontally using a carx variable that increments in the while loop — giving the illusion of motion. I even added Brain.playSound(headlightsOn) for some extra flair.

🎂 Birthday Cake
The birthday cake was the most technical screen design — I used a massive pixel coordinate list (int list[6989][2]) to draw a detailed cake image pixel by pixel on the screen, then printed "Happy Birthday!<3" in mono15 font underneath. Plotting thousands of individual points to form an image taught me a lot about how graphics rendering actually works at a low level.

☁️ Cloud
Similar to the birthday cake, the cloud scene uses a hand-mapped list of 1,128+ pixel coordinates to draw a detailed cloud outline on a white background. The coordinates trace the outer contour of the cloud shape, and a for loop renders each pixel one at a time.
The three themes were connected through button inputs: pressing the left button triggered the car animation and pressing the right button launched the birthday cake scene.


<h4 class="toc_title">Step 2: Fall Screen Design</h4>
For this project, I created a full Halloween/autumn-themed animated display with multiple moving elements all running at the same time using VEX's thread system.


There are four animated components:
🍂 Falling Leaves — Six colored circles (red, orange, yellow) representing autumn leaves fall downward using a leaf variable. When they reach the bottom of the screen, the variable resets so they fall again in a continuous loop.

🌙 Moving Moon — A yellow circle representing the moon drifts slowly across the top of the screen using a moon variable. When it exits the right side, it resets to the left.
👻 Ghost — A white circle with two black "eye" circles glides across the screen from right to left. Every half second, the ghost's position shifts and the screen clears, creating a spooky floating effect. When it disappears off the left edge, it resets to the right side.

🎃 Pumpkin — Three overlapping orange circles form a jack-o'-lantern body, with a short vertical line for the stem. The pumpkin stays fixed at the bottom of the screen as everything else animates around it.

Each animation ran in its own thread, triggered by a different button on the brain — left button for moon movement, right button for the ghost, and the check button for the falling leaves.


<h4 class="toc_title">Step 3: Distance Sensing</h4>

The final and most advanced project combined everything — screen design, animation, driving code, and sensor input — all working together in real time.
The robot uses a distance sensor (Distance7) to detect objects in front of it. Here's how the logic works:

- If an object is detected closer than 15 inches, the robot stops, reverses 200mm, and turns right 90 degrees to avoid the obstacle. At the same time, the brain screen flashes a "CAUTION!" warning with two red pulsing circles animated up and down the screen.
- If no obstacle is nearby, the robot drives forward continuously, and the brain screen displays the fall Halloween animation — the moon, leaves, ghost, and pumpkin — all running in a background thread while the robot moves.

This project was the most exciting to build because it felt like a real autonomous system: the robot is independently sensing its environment, making decisions, and reacting — all while displaying a fun animated UI on its screen.


<h4 class="toc_title">Reflections</h4>

Building this code library taught me so much — from basic functions and loops, to animation logic using variables and while loops, to multithreading and sensor-driven decision-making. Looking back at Project 1 versus Project 4, it's wild to see how much more complex and creative the code became over time. I'm really proud of what I built, and I can't wait to keep learning!


