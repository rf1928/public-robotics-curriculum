---
id: reproducible-replay
title: Reproducibility through replay
group: systems-plumbing
depth: evaluate
week: 2026-10-w3
quiz: |
  1. What can open-loop log replay tell you about a run, and what can it not? Why does testing planning and control need closed-loop re-simulation instead?
  2. In a Gazebo and ROS 2 setup, where does the simulated clock the nodes run on come from, and what do the nodes' timestamps follow if the bridge does not carry it? Why does a replay need that controlled clock instead of running as fast as the hardware allows?
  3. What goes wrong in a replay that runs on wall time: what happens to timestamps and to transform lookups, and why?
criterion: |
  **Checks:** a replay you can trust, and why it depends on simulated time.

  **Write:** a note (about half a page) on why simulated time versus wall time matters, built on the plot from your own broken replay (the week's break-it, replayed without sim time): what disagreed, and what fixed it.

  **Link:** a bag you recorded and replayed with timestamps and transforms agreeing, and the plot from the broken replay.
---
A recorded run is the only way to look at the same failure twice. rosbag2 writes MCAP files that can be replayed into the same system or opened in Foxglove and PlotJuggler. Replay only reproduces the run if the system runs on the recorded clock: simulated time versus wall time decides whether timestamps and transforms line up.

**Field tie.** Remote support starts from a log, not from the vehicle; every later triage in this plan depends on a replay you can trust.
