---
id: symptoms-downstream
title: Symptoms appear downstream of their causes
group: sensing-and-fusion
depth: evaluate
week: 2026-11-w4
quiz: |
  1. Why does a fault rarely show where it starts? Use the autonomy loop to explain.
  2. A stamp offset, a rotated extrinsic, a dropped topic and a wrong covariance can all end as a bad position estimate. For each, name one early sign in a bag that tells it apart from the others.
  3. Why does triage work backwards from the symptom, through estimation, frames and time, rather than forwards from the sensors?
criterion: |
  **Checks:** working back from a symptom to its cause, on faults you did not choose.

  **Write:** a walk-through (about two pages) of "the vehicle drifts off course after twenty minutes", working backwards through estimation, frames and time, with your own bags and journal entries as the examples.

  **Link:** a journal entry recording at least one blind drill diagnosed correctly before you checked the answer.
---
In the autonomy loop a fault rarely shows where it starts: a stamp offset, a rotated extrinsic, a dropped topic or a wrong covariance all surface later as a bad position estimate. Triage works backwards from the symptom through estimation, frames and time to the cause, with the six-step method from the plan tab. The blind drill is the closest thing to a real remote-support ticket you can build at home.

**Field tie.** The month's anchor: why did the vehicle think it was somewhere else, diagnosed from its logs.
