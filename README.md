# Golden Retriever Walker: ACT Grasp (my code)

The part of our Corgi × YC hackathon robot walker that I wrote: recording
teleoperated demonstrations on an SO-101 arm with LeRobot, the ACT
imitation-learning setup, and the grasp-policy inference loop.

| Path | What it is |
|---|---|
| `scripts/record_5.ps1`, `scripts/record_40.ps1` | `lerobot-record` commands for the leader→follower teleop dataset (wrist camera, 30 fps) |
| `dataset_meta/` | Metadata of the recorded dataset `walker_pill_grasp_v2`: 40 episodes, 10,282 frames at 30 fps (frames and video not included) |
| `configs/act/` | The saved ACT policy and training configuration. It is configured for 50,000 steps; the checkpoint committed to the team repo is from step 15,000. |
| `scripts/run_grasp_policy.py` | 30 Hz inference loop: runs the ACT policy, detects a grip when the gripper stalls on the bottle, then hands off to a scripted retract |
| `scripts/check_dataset.py` | Sanity checks on a recorded dataset |
| `scripts/arm_bringup.py`, `scripts/arm_health.py` | SO-101 bring-up and servo health checks over LeRobot's Feetech bus |
| `docs/TRAINING_GRASP.md` | Plan for the grasp: learned ACT pick, scripted place |

**Not standalone.** These scripts import `robot.arm`, `robot.config` and
`robot.poses` from the team repository (mostly written by Andrew Wang). Run
them from a checkout of the team repo.

## Credits
- Team: Tarun Malarvasan (depth-camera controls), Jerry Li (walker chassis, motor-control firmware), Andrew Wang.
- Built on [LeRobot](https://github.com/huggingface/lerobot) (Hugging Face, Apache-2.0) and ACT (Action Chunking with Transformers, Zhao et al.).
- Some of my commits in the team repo were made with Cursor's AI assistant (marked by co-author trailers there).

## Provenance
Files copied unchanged from the team repository
[jerryli08/corgi-hackathon](https://github.com/jerryli08/corgi-hackathon) at
commit `e683997`. Only files whose lines are by me per `git blame` are included.
License: not yet chosen.
