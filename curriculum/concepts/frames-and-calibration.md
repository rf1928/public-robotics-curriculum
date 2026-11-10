---
id: frames-and-calibration
title: Frames, rigid-body transforms and extrinsic calibration
group: systems-plumbing
depth: evaluate
week: 2026-11-w2
quiz: |
  1. Why does the order of rotations matter? When would you use a rotation matrix, Euler angles or a quaternion, and what is the trap with Euler angles?
  2. What do REP 103 and REP 105 fix? Say what map, odom and base_link are, and why odom may drift but must not jump.
  3. What is the difference between a static and a dynamic transform? What does an extrinsic calibration, with its lever arm, say about a sensor?
  4. ROS uses east-north-up; marine systems mostly use north-east-down. What goes wrong at that boundary, and how would you catch it?
criterion: |
  **Checks:** frame and calibration faults, diagnosed from their symptoms in a replay.

  **Write:** journal entries that together diagnose each of these from the symptoms in a replayed bag: a rotated extrinsic, a flipped IMU axis, a wrong frame_id, a late static transform and a zero lever arm. For each: the symptom, the cause, and how you confirmed it.

  **Link:** your rig's URDF.
---
Opens with a refresher of under an hour on rotation matrices, Euler angles and quaternions, and why the order of rotations matters. REP 103 fixes units and axis conventions; REP 105 fixes map, odom and base_link. Transforms are static or dynamic, and extrinsic calibration with its lever arms says where each sensor sits on the body. ROS uses east-north-up while marine and aviation systems mostly use north-east-down, and conversion errors at that boundary are a classic integration bug.

**Field tie.** A multibeam patch test calibrates latency, roll, pitch and yaw offsets between the sonar and the motion sensor, which is weeks 1 and 2 performed on a vessel. Every survey starts with one.
