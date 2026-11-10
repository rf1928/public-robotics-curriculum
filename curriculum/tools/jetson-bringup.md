---
id: jetson-bringup
title: Jetson bring-up
first_week: 2026-10-w4
criterion: >
  Brings up an NVIDIA Jetson Orin with JetPack, ROS 2 Lyrical in a container and sensor drivers, and
  streams live topics to a remote laptop through foxglove_bridge.
---
JetPack 7.2 is Ubuntu 24.04 and Lyrical ships only for 26.04, so ROS runs in a Lyrical container on the Jetson, not on the host. Pulled forward from November week 1; if the hardware is late it stays there.
