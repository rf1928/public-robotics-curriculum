---
id: sensor-modalities
title: What each sensor measures, and how it fails
group: sensing-and-fusion
depth: explain
week: 2026-10-w4
quiz: |
  1. For an IMU, a camera with visual odometry, and GNSS: what does each measure, at roughly what rate, and how does its error behave over time (grows without bound, or stays bounded)?
  2. Name one condition that makes each of the three fail, and the symptom you would see.
  3. Underwater there is no GNSS. What does an AUV's navigation suite use instead (INS, Doppler velocity log, USBL or LBL, pressure sensor), and what does each contribute?
  4. Why does sensor fusion exist at all? Answer in terms of timescales.
criterion: |
  **Checks:** what each sensor measures and how it fails, read from real datasheets.

  **Write:** a table (about a page) covering the rig's camera, IMU and GNSS receiver and an AUV's navigation suite: for each sensor, what it measures, at what rate, how its error grows, and the symptom that shows it failing.

  **Link:** the datasheets you read in this week's drift-budget lab.
---
Taken before the datasheet lab, so the datasheets can be read end to end. Each sensor measures something different, and its error behaves differently. An IMU measures angular rate and specific force at hundreds of hertz; it is smooth over seconds, but integrating it turns bias into drift that grows without bound. A camera, and a depth camera such as the rig's Gemini 335, sees structure; visual odometry estimates motion from it and fails in low texture, motion blur and poor light. GNSS gives absolute position at a few hertz with error that does not grow, but it needs open sky and suffers from multipath. Wheel or velocity odometry sits in between.

Underwater, GNSS is gone. An AUV pairs an inertial navigation system with a Doppler velocity log that measures speed over the seabed, acoustic positioning (USBL, LBL) that fixes position from outside, a pressure sensor for depth, and sonars for mapping. Fusion exists because no single sensor is good on every timescale.

**Field tie.** A datasheet is a list of these error figures. Reading an AUV and a USV datasheet this week is the first time the plan asks you to judge a sensor suite the way a customer's engineer would.
