---
id: reproducible-replay
title: Reproducibility through replay
group: systems-plumbing
depth: evaluate
week: 2026-10-w3
quiz: |
  1. What can open-loop log replay tell you about a run, and what can it not? Why does testing planning and control need closed-loop re-simulation instead?
  2. What is the difference between simulated time and wall time in ROS 2? During a replay, which clock should the nodes run on, and where does that clock come from?
  3. What goes wrong in a replay that runs on wall time: what happens to timestamps and to transform lookups, and why?
criterion: |
  **Checks:** a replay you can trust, and why it depends on simulated time.

  **Write:** a note (about half a page) on why simulated time versus wall time matters, built on the plot from your own broken replay (the week's break-it, replayed without sim time): what disagreed, and what fixed it.

  **Link:** a bag you recorded and replayed with timestamps and transforms agreeing, and the plot from the broken replay.
---
A recorded run is the only way to look at the same failure twice. rosbag2 writes MCAP files that can be replayed into the same system or opened in Foxglove and PlotJuggler. Replay only reproduces the run if the system runs on the recorded clock: simulated time versus wall time decides whether timestamps and transforms line up.

**Field tie.** Remote support starts from a log, not from the vehicle; every later triage in this plan depends on a replay you can trust.
