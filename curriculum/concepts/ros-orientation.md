---
id: ros-orientation
title: What ROS 2 is, and when a team uses it
group: systems-plumbing
depth: explain
week: 2026-10-w2
quiz: |
  1. ROS 2 is not an operating system. What is it, and what problem does it solve for a team whose robot is many programs written by different people?
  2. Name its layers, from the code you write down to the network: client library, middleware interface, DDS or Zenoh. What does each one do?
  3. What does a team gain by choosing ROS 2, and what does it cost them? Name one kind of system that would not use it, and say why.
criterion: |
  **Checks:** what ROS 2 is and is not, the problem it solves, and what a team gains and pays by choosing it, explained to someone outside robotics.

  **Write:** a note (about a page) for an engineer new to robotics covering those points, with one kind of system that would not use ROS 2 and why.

  **Link:** three public job postings or project pages that name ROS 2, as evidence of where teams use it.
---
The hour week 1 set aside for this, taken in week 2 before the distributed real-time material. ROS 2 is not an operating system: it is middleware, a set of conventions, a toolset and a package ecosystem running on Linux. The problem it solves is that a robot is many programs written by different people (drivers, estimators, planners, controllers) that must exchange data; ROS 2 gives them common message types, a way to find each other, and tools to record, replay, visualise and inspect what passes between them. The layers: client libraries (rclpy, rclcpp) over a middleware interface that runs DDS by default, with Zenoh as an alternative; packages and workspaces built with colcon; launch files and parameters to assemble a system; REPs to fix shared conventions such as units and frames. Releases are distributions pinned to an Ubuntu version: Lyrical is the long-term-support release for Ubuntu 26.04, and Jazzy, the previous one, is pinned to 24.04. That pinning is why the Jetson, whose JetPack is Ubuntu 24.04, runs Lyrical in a container. ROS 1, with its central master and no quality of service, is what most older material describes. Gazebo is a separate simulator joined to ROS 2 by a bridge.

Where it is used and where it is not: research, prototyping, mobile and field robots, and much marine autonomy run on it; Autoware builds road autonomy on it. Production robotaxi stacks commonly run in-house middleware, microcontroller firmware reaches ROS 2 only through micro-ROS, and hard real-time control loops usually sit below it.

**Field tie.** "ROS 2" is one of the phrases robotics job postings keep using. Knowing what a team means by it, and what they leave out of it, is the first conversation with a robotics customer or interviewer.
