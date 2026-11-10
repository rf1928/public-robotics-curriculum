---
id: distributed-realtime
title: A robot is a distributed real-time system
group: systems-plumbing
depth: evaluate
week: 2026-10-w2
quiz: |
  1. Why is a robot a distributed system? Name what can happen to a message between two processes, and say why a sender cannot tell a lost message from a slow or dead peer.
  2. What does DDS give ROS 2 (discovery, quality of service, the wire protocol), and what does ROS add on top of it?
  3. Reliability, durability, history depth, namespace and domain ID all decide whether two nodes talk. Pick two and say how a mismatch makes a topic go silent with no error.
  4. When would you choose best effort over reliable, for example over a lossy radio or satellite link, and what do you give up?
criterion: |
  **Checks:** why a ROS 2 topic can go silent with no error, shown with causes you reproduced yourself.

  **Write:** an explanation (about a page) of three causes from the week's break-it (QoS mismatch, wrong namespace, different domain IDs, history depth of one). For each: the symptom you saw, why the middleware stayed silent, and how you would spot it on a robot you did not build.

  **Link:** each cause to the break-it journal entry where you reproduced it.
---
A robot is not one program but many processes exchanging messages over a network, and data can arrive late, get lost, or arrive silently wrong. ROS 2 is middleware running over DDS, not an operating system: nodes, topics, services, actions, parameters and launch files sit on top of DDS discovery and domain IDs. Quality-of-service profiles (reliable versus best effort, durability, history depth) and namespaces decide whether two nodes ever actually talk.

**Field tie.** A satellite or radio link is where quality of service stops being academic: best effort over a lossy link, and discovery traffic that swamps a narrow one. Remote monitoring of a robotaxi or a warehouse fleet has the same problem.
