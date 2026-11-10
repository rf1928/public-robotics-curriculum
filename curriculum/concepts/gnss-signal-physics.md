---
id: gnss-signal-physics
title: GNSS signal physics and the antenna
group: sensing-and-fusion
depth: explain
week: 2026-11-w3
quiz: |
  1. L1 has a wavelength of about 19 cm and L2 about 24 cm. Why does the wavelength set the size of the patch antenna and its ground plane?
  2. How does right-hand circular polarisation help the antenna reject multipath? Why do two frequencies let the receiver remove the ionospheric delay?
  3. Name what sets a fix's accuracy, from sky view to the corrections. Why does an RTK solution that stays float in open sky usually point at the antenna or its mounting, not the software?
criterion: |
  **Checks:** why the antenna, its ground plane and its mounting set most of an RTK fix's quality.

  **Write:** a note (about a page) explaining that, and naming the mounting and cabling pitfalls by the symptom each one produces.

  **Link:** your rig's antenna setup, or the week's ground-plate journal entry (antenna on versus off its ground plate).
---
Opens with half an hour on waves, polarisation and reflection. L1 at 1575.42 MHz has a wavelength of about 19 cm and L2 at 1227.6 MHz about 24 cm, which sets the size of the patch and its ground plane. GNSS signals are right-hand circularly polarised and a single reflection flips the handedness, which is how the antenna rejects much of the multipath; ionospheric delay scales roughly with 1/f², so two frequencies let the receiver remove it. Accuracy is set by sky view and geometry, multipath, phase centre stability, cable losses, and for RTK the distance to the correction source and the age of the corrections. An RTK solution that stays float in open sky usually points at the antenna or its mounting, not the software; the F9P's jamming and interference indicators are known at Explain depth only.

**Field tie.** The RTK track is this week's ground truth, and most of its quality is fixed before any software runs.
