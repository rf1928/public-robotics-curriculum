---
id: planning-hierarchy
title: The planning hierarchy
group: decision-under-uncertainty
depth: explain
week: unscheduled
criterion: >
  Demonstrated when you've written a note (about a page) on the global, local and
  behaviour layers, the rate each runs at and the job each does, and why D* Lite suits a
  map that changes, illustrated with a planner run of your own once this concept is
  scheduled.
---
Not scheduled yet: decided when the December lesson plan is written. A global planner routes through the known map in seconds (A*, D* Lite, hybrid A*, RRT*); a local planner avoids what the sensors just found at 10-50 Hz (dynamic window, timed elastic band, MPPI); a behaviour layer decides what the goal currently is, on events. D* Lite replans incrementally when the map changes, which is the partial-information case.
