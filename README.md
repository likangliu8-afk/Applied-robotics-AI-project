[README.md](https://github.com/user-attachments/files/33658360/README.md)
# Applied Robotics and AI Project

Course deliverables, lab notes and code for the **Applied Robotics and AI**
practical course (BEng Robotics & AI, University of Hertfordshire).

This repository collects the per-practical (P1…Pn) submissions, ROS node
examples and supporting notes produced throughout the term.

---

## Prerequisites

- **ROS 2** (e.g. Humble) installed on the target machine
- **Python 3** (3.10+ recommended)
- A Linux environment (Ubuntu 20.04 / 22.04) for full ROS support

Install ROS 2 following the official distro-specific documentation:

```bash
# Example: source the workspace after every new shell
source /opt/ros/humble/setup.bash
```

## Repository Layout

```
applied-robotics-ai-project/
├── docs/            # Per-practical notes and write-ups
├── img/             # Evidence screenshots and figures
├── nodes/           # ROS node examples
│   └── talker.py    # P3 pub/sub demo – publisher node
├── .gitignore
└── README.md
```

| Path | Purpose |
| --- | --- |
| `docs/` | Lab notes and per-practical reports |
| `img/` | Screenshot / figure evidence for submissions |
| `nodes/` | Standalone ROS node scripts used in the practicals |

## Nodes

### `nodes/talker.py` — P3 pub/sub demo (publisher)

A minimal ROS 2 publisher that publishes a string to the `/chatter` topic
at 0.5 Hz using `rospy`.

**Topic**

| Field | Value |
| --- | --- |
| Topic | `/chatter` |
| Type | `std_msgs/String` |
| Rate | 0.5 Hz (queue size 10) |

**Run it**

```bash
# Terminal 1 – start the talker
ros2 run <package> talker.py
# or, if registered as a rosrun entry point:
ros2 run talker_node talker
```

**Verify on a second terminal**

```bash
# Echo the topic to confirm the 0.5 Hz stream
ros2 topic echo /chatter
```

Expected output:

```
data: Hello from P3 talker
---
```

## Workflow & Conventions

- One commit per practical change; branch naming follows the
  `feature-p3-pubsub` style.
- Notes live in `docs/` and screenshots in `img/`; avoid committing
  large binaries or IDE state (see `.gitignore`).
- Node scripts are kept standalone under `nodes/` until they are
  packaged into a proper ROS package.

## .gitignore

The repository ignores the usual ROS + Python artifacts:

```
__pycache__/
*.pyc
venv/
build/
.catkin_tools/
*.rosbag
*.db3
.idea/
.vscode/
.DS_Store
```

## Contributing / Submission Checklist

For each practical, before pushing:

1. [ ] Node script under `nodes/` (or inside the ROS package)
2. [ ] Notes written in `docs/`
3. [ ] Evidence screenshots added to `img/`
4. [ ] Topic / node verified with `ros2 topic echo` / `ros2 node list`
5. [ ] Commit message references the practical number (e.g. `P3: …`)

## Licence

Course work for internal academic use — University of Hertfordshire,
Applied Robotics and AI module.
