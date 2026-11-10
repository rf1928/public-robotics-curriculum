---
id: feedback-control
title: Feedback control
group: control-and-actuation
depth: explain
week: 2026-10-w3
quiz: |
  1. In a second-order system such as the damped spring-mass, what do the damping ratio and the natural frequency decide about the response: overshoot, oscillation, settling time?
  2. What does each PID term do? Why does the derivative term amplify sensor noise, and why does the integral term remove the steady error a constant disturbance leaves?
  3. What is integral windup? Say what the integral does while the actuator is saturated, and what that does to the response once it is not.
  4. What does feedforward do that feedback cannot, and the other way round? In a cascade, why must the inner loop be faster than the outer one?
criterion: |
  **Checks:** integral windup, shown on your own tuning and explained from the plot.

  **Write:** an explanation (about a page) of integral windup built on your own plot from this week's lab, where you tuned a heading autopilot for a surface vessel in Fossen's simulator, added a constant current and limited the rudder. Say what the plot shows while the rudder is at its stop, why the integral causes the overshoot that follows, and one remedy (anti-windup, or feeding the current forward).

  **Link:** the plot and the tuned gains.
---
Opens with a refresher of under an hour: first- and second-order differential equations, damping and oscillation in the damped spring-mass system, and what a transfer function expresses. Then PID: what each term does, why the derivative term amplifies noise, and why the integral term winds up when an actuator saturates. Cascaded loops put a fast inner loop under a slow outer one; feedforward predicts from the model while feedback corrects from the error.

**Field tie.** A vessel's heading autopilot fighting a cross-current is the same windup you produce in the lab. A robotaxi's steering controller is the inner loop of a cascade under its planner.
