---
id: time-sync
title: Time and clock synchronisation
group: systems-plumbing
depth: evaluate
week: 2026-11-w1
quiz: |
  1. What is the difference between a message's header stamp and the time it was received? Which one should a fusion filter use, and why?
  2. The rig has three clocks: GNSS time, the camera's clock and the Jetson's system clock. How are they brought into agreement, and what do NTP, PTP, a GNSS pulse-per-second and chrony each contribute?
  3. Why do tens of milliseconds of skew turn a working filter into a drifting one? When is that skew harmless and when does it decide everything (compare a walking cart with acoustic ranging at 1,500 m/s)?
criterion: |
  **Checks:** every timestamp on the rig accounted for, and clock faults diagnosed from their symptoms.

  **Write:** a note (about a page) that accounts for every timestamp in a bag from the rig: which clock stamped it, and the gap between header stamp and receipt time for each topic.

  **Link:** the bag, your header-stamp-versus-receipt plot, and the week's break-it journal entries that diagnose a 50 ms camera stamp offset and a skewed system clock from their symptoms alone.
---
A message's header stamp is not the time it was received. The rig has three clocks: GNSS time from the satellites, the camera's internal clock, and the Jetson's system clock. NTP, PTP and a GNSS pulse-per-second are covered at concept level, with what chrony does with them. Tens of milliseconds of skew turn a working fusion filter into a drifting one.

**Field tie.** Acoustic positioning is time of flight at roughly 1,500 m/s, so one millisecond of clock error is about 1.5 metres of range error. Timing is not a detail underwater; it is the measurement.
