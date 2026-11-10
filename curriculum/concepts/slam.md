---
id: slam
title: SLAM
group: world-representation
depth: explain
week: 2026-11-w4
quiz: |
  1. Why are building the map and locating yourself in it the same problem?
  2. What does the front end of a SLAM system do? What does the back end do with its graph of poses and constraints?
  3. What is a loop closure, and why does the whole map snap when one is found?
criterion: |
  **Checks:** front end, back end and loop closure, seen in your own run.

  **Write:** a note (about a page) on those three, built on a loop closure from your own RTAB-Map run.

  **Link:** a plot comparing the RTAB-Map track against the filter-only track from week 3.
---
Building the map and locating yourself inside it are the same problem, because each depends on the other. A front end matches features between frames; a back end optimises a graph of poses and constraints; loop closure corrects accumulated drift when the robot recognises somewhere it has been, and the whole map snaps. ORB-SLAM3, FAST-LIO2, LIO-SAM and GTSAM are worth reading about and not worth building at Explain depth.

**Field tie.** Terrain-aided navigation on an AUV is loop closure against a prior map when no GNSS is available.
