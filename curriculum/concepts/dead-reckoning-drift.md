---
id: dead-reckoning-drift
title: Dead reckoning and the drift budget
group: sensing-and-fusion
depth: explain
week: 2026-10-w4
quiz: |
  1. Why does dead reckoning drift? Explain how integrating an IMU turns a small constant bias into a position error that keeps growing.
  2. What does a Doppler velocity log change about that growth? What do USBL and LBL acoustic positioning do that a velocity log cannot?
  3. What is a drift budget, and why is it the number that decides what an underwater survey can promise?
criterion: |
  **Checks:** the drift budget, worked out from a datasheet and explained to a customer.

  **Write:** one page for an intelligent non-technical customer on what a drift budget is and why it decides what an underwater survey can promise.

  **Link:** your own working from this week's lab: how far the AUV travels before position error passes 10 metres, with and without its velocity log.
---
GNSS disappears underwater, so position comes from dead reckoning: inertial navigation integrates its errors and drifts. A Doppler velocity log slows the drift; ultra-short and long baseline acoustic positioning reset it from outside. The drift budget is the single number that decides what a survey can promise.

**Field tie.** The October one-pager. In November week 3 the same budget is worked out for your own walk after a GNSS dropout.
