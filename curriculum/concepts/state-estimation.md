---
id: state-estimation
title: State estimation under uncertainty
group: sensing-and-fusion
depth: evaluate
week: 2026-11-w3
quiz: |
  1. An extended Kalman filter predicts, then corrects. What does each step use, and what happens to the covariance in each?
  2. What is the innovation? What does a diverging filter look like in a plot?
  3. robot_localization runs two filters. What does the odom-frame filter fuse, what does the map-frame filter add, and what does navsat_transform do between them?
  4. What happens when the GNSS covariance is set far too small? How much is an RTK float anchor worth compared with a fixed one?
criterion: |
  **Checks:** diagnosing a fusion filter from its output, and finding where its error starts rather than where it shows.

  **Write:** a journal entry that diagnoses the zero-lever-arm bag from its symptoms alone, and a note (about a page) with your own plot of the fused track against RTK ground truth that shows where the error starts growing, and why there.

  **Link:** the plot and the bags it comes from.
---
Opens with a refresher of under an hour on Gaussian distributions, covariance matrices and the matrix algebra the filter is written in. An extended Kalman filter predicts from motion and corrects from measurements; covariance is its statement of how sure it is, and innovation is the gap between what it expected and what it saw. A diverging filter has a recognisable shape in a plot. robot_localization's two-filter pattern runs a continuous estimate in the odom frame and a GNSS-anchored one in the map frame, joined by navsat_transform; RTK float versus fixed decides how much the anchor is worth.

**Field tie.** Losing GNSS is what happens when an AUV dives, and INS aided by a Doppler velocity log is this filter with the DVL in place of visual odometry. A robotaxi in an urban canyon loses GNSS the same way.
