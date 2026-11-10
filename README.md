# Field robotics curriculum: from ROS 2 basics to remote triage

A self-paced, two-month curriculum for an engineer moving into deploying and supporting autonomous systems: mobile robots, marine vehicles, robotaxis. It is built around one question a field engineer gets asked: *why did the vehicle think it was somewhere else?* By the end you answer it from the vehicle's own logs.

Every week pairs concepts with hands-on work:

- **Lab:** build the thing.
- **Break-it:** break it on purpose, the way it breaks in the field, and write a *failure journal* entry for each break.
- **Field tie:** map what you just did onto a real deployment (an AUV losing GNSS, a vessel autopilot in a cross-current, a robotaxi in an urban canyon).

Each month ends with a checkpoint you can show someone.

Everything here is plain Markdown and YAML. There's nothing to sign up for and no access to request. Clone it and start at week 1.1. The optional [review agent](#review-agent-optional-paid) checks your quiz answers with Claude.

## The plan

About 75 hours over eight weeks, at 7 to 11 hours a week.

| Week | Title | Hours | Goal | Concepts |
|---|---|---|---|---|
| 1.1 | Setup | 8 | A dev machine running ROS 2 Lyrical and Gazebo, and the rig hardware ordered. | — |
| 1.2 | ROS 2 fundamentals | 9 | Explain how data moves through a ROS 2 system, and why it sometimes silently does not. | ros-orientation, autonomy-stack, distributed-realtime |
| 1.3 | Replay and control | 9 | Record and replay a run, and explain why controllers overshoot, oscillate and wind up. | feedback-control, reproducible-replay |
| 1.4 | Thin maritime pass and Jetson bring-up | 9 | Hold a first conversation about marine navigation, and have the Jetson running before month 2 starts. | sensor-modalities, dead-reckoning-drift |
| 2.1 | Clocks and bags | 11 | The rig records one clean bag with all three sensors, and you can explain every timestamp in it. | time-sync |
| 2.2 | Frames and calibration | 11 | A correct TF tree for the rig, and the ability to recognise a wrong one from its symptoms. | frames-and-calibration |
| 2.3 | State estimation | 11 | A fused position estimate you can compare against ground truth, and a feel for how it fails. | state-estimation, gnss-signal-physics |
| 2.4 | SLAM and the blind drill | 7 | Watch a loop closure correct drift, and diagnose an unseen fault from a bag the way a remote-support ticket arrives. | slam, symptoms-downstream |

**Month 1, the anchor:** who pays for autonomy, what they are buying, and what they are afraid of. The technical base: ROS 2, replay, control, and the drift budget.
**Month 2, the anchor:** remote triage. Why did the vehicle think it was somewhere else, diagnosed from its logs.

Three concepts (`exploration`, `maps-and-costmaps`, `planning-hierarchy`) are written but not yet scheduled; they belong to a later month.

## How the files fit together

```
curriculum/
  months/      one file per month: the anchor question and the checkpoint
  weeks/       one file per week: hours, goal, concepts, tools, and the activities with their steps
  concepts/    one file per concept: depth, quiz, criterion, and a short explanation
  tools/       one file per tool: what "knowing it" means
  materials/   study materials for a concept, tool or activity: links, minutes, and why each one matters
  groups.yaml  the five competency groups
review/        the optional review agent
notes/         your own quiz answers (yours to fill)
```

Every file starts with YAML front matter, so the curriculum can be read by hand or by a program.

- **depth** says how far a concept should go: `describe` (name the parts), `explain` (the mechanism, in your own words) or `evaluate` (when it holds, when it doesn't, and what you'd choose).
- **quiz** checks understanding. Answer it in writing before moving on.
- **criterion** (the *practical*, as the study notes call it) checks you can do it. It says what to write and what to link (a plot, a bag, a journal entry) to show the concept in your own work.
- **materials** are tiered `required`, `recommended` or further reading. Many entries also carry a `plan`: `first` (read before you start), `when-needed` (open at a named step) or `further`. Materials exist so far for the month 1 concepts and activities.

### Working through a week

1. Open the week file in `curriculum/weeks/`. Read its goal, and the concept and tool files it names.
2. Read the `first` materials for those concepts (in `curriculum/materials/`).
3. Do the lab, then the break-it. Write a failure journal entry for each break: the symptom, what you suspected, the cause, and how you'd spot it faster next time.
4. Answer each concept's quiz in `notes/<concept-id>.md`, and review it if you like (below).
5. Do the field tie, and the write-up the criterion asks for.

Keep your notes, journal, plots and bags in a git repository of your own. The month checkpoints ask you to link back to them.

## Hardware

Month 1 needs only a computer. Month 2 uses a small sensor rig on a cart:

- An Ubuntu 26.04 machine (native install) with ROS 2 Lyrical and Gazebo Jetty.
- An NVIDIA Jetson Orin (JetPack 7.2; ROS 2 runs in a Lyrical container).
- An Orbbec Gemini 335 depth camera, which has an IMU.
- A u-blox ZED-F9P RTK GNSS receiver, with an antenna on a ground plate and NTRIP or PointPerfect corrections.
- A cart with a mast for the antenna, and a tape measure.

If you have no rig, run the month 2 labs on public datasets (week 2.4 already uses EuRoC), and do the break-its on recorded bags.

## Review agent (optional, paid)

`review/review.py` checks your answer to a concept's quiz with Claude Sonnet. It reads the concept and its study materials, fetches the linked pages itself, and writes advisory feedback per question: what's correct, what's overstated or imprecise, what's missing, and how deep the answer goes against the concept's target. It never grades.

**It needs an Anthropic API key, and every check is billed to that key, per use.** Expect roughly $0.05 to $0.10 per check. Setup, costs and a free alternative: [review/README.md](review/README.md).

```bash
python3 -m pip install pyyaml
python3 review/review.py new distributed-realtime      # creates notes/distributed-realtime.md from the quiz
export ANTHROPIC_API_KEY=sk-ant-...                    # your own key
python3 review/review.py check distributed-realtime    # paid call; writes notes/distributed-realtime.review.md
```

## Licence

The curriculum text (`curriculum/`, and this README) is under [CC BY 4.0](LICENSE-CONTENT). The review agent's code is under [Apache 2.0](LICENSE). The study materials link to third-party pages, which keep their own terms.
