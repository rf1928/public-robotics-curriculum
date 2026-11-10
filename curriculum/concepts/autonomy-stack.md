---
id: autonomy-stack
title: The autonomy stack, end to end
group: systems-plumbing
depth: explain
week: 2026-10-w2
quiz: |
  1. Name the layers of the autonomy loop in order, from sensors to actuators, and say what each layer hands to the next.
  2. Give a rough rate for the IMU, the controller and the planner. Why does the loop run as many programs at different rates rather than as one program?
  3. Why does a fault in one layer usually show up in a later layer? Give one example.
criterion: |
  **Checks:** the layers of the autonomy stack, what flows between them, and where each topic of this plan sits on it.

  **Write:** a note (about a page) around your own diagram of the stack from sensors to actuators. Place every concept and tool of October and November on it, and mark where the three unscheduled concepts (maps and costmaps, the planning hierarchy, exploration) would go.

  **Link:** the diagram, if it is a separate file.
---
The map the rest of the plan hangs on, taken in week 2 alongside what ROS 2 is. An autonomous vehicle runs a loop: sensors measure; state estimation turns noisy measurements into a belief about where the vehicle is and how it is moving; a world representation holds what it knows about its surroundings; planning decides where to go and how, from a route down to the next second of motion; control turns that into actuator commands; and the vehicle moves, which changes what the sensors see. Underneath every layer runs the plumbing: messages, clocks, frames and logs. The curriculum's groups are these layers, and each week works on one of them.

Each layer runs at its own rate, from a control loop at hundreds of hertz to a route planner every few seconds, and a fault in one layer usually surfaces in a later one. That is why November's triage works backwards from a symptom.

**Field tie.** A robotaxi, a warehouse robot and an AUV run the same loop with different sensors and different consequences. A customer's question ("why did it stop?", "why is it off course?") points at one layer; knowing the stack is knowing where to start looking.
