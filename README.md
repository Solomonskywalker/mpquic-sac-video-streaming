# Deep Reinforcement Learning for Adaptive Multipath QUIC Video Streaming

**Using Soft Actor-Critic (SAC) for Adaptive Traffic Scheduling over Wi-Fi and LTE Networks**

## 1. Project Overview

This project explores the use of Deep Reinforcement Learning (DRL) to improve video streaming over Multipath QUIC (MPQUIC).

The main objective is to develop a Soft Actor-Critic (SAC) agent that can adaptively distribute video traffic across heterogeneous network paths, particularly Wi-Fi and LTE/4G/5G connections.

The agent will use network information obtained from MPQUIC, including bandwidth, round-trip time (RTT) and packet loss, to make traffic-scheduling decisions. Its performance will be evaluated based on video Quality of Experience (QoE), rebuffering time, throughput and packet reordering.

The implementation will use Go-MPQUIC for multipath communication and Python for reinforcement learning.

## 2. Research Objectives

The project aims to:

1. Develop an SAC-based scheduler for adaptive MPQUIC traffic distribution.
2. Use network telemetry as observations for the reinforcement learning agent.
3. Design a continuous action space for multipath traffic scheduling.
4. Evaluate the agent under changing Wi-Fi and LTE network conditions.
5. Compare its performance against conventional scheduling methods.
6. Investigate its effect on video-streaming QoE and network performance.

## 3. Proposed Methodology

The implementation is divided into four main components.

### 3.1 MPQUIC Network Testbed

A Go-MPQUIC testbed will be established to support communication over multiple network paths.

Linux network emulation tools will be used to create separate Wi-Fi and LTE paths. Bandwidth, delay, jitter and packet loss will be varied to represent different network conditions.

Publicly available mobile-network traces will also be investigated for use in network-condition replay.

### 3.2 Video Streaming Environment

A video server and streaming client will be configured to generate traffic over the MPQUIC connection.

The streaming environment will provide the traffic and performance measurements needed to evaluate the scheduling strategies.

### 3.3 SAC Agent

The reinforcement learning component will be developed in Python using PyTorch and Stable-Baselines3.

The agent will interact with the network through three main elements:

- **Observations:** Available network telemetry, including bandwidth, RTT, packet loss and other path statistics.
- **Actions:** Continuous scheduling decisions that influence traffic distribution across the available paths.
- **Rewards:** Feedback based on throughput, rebuffering, packet reordering and video-streaming QoE.

The exact interface between the Python agent and the Go-MPQUIC scheduler will be determined during implementation.

### 3.4 Experimental Evaluation

The SAC scheduler will be compared against conventional multipath scheduling approaches, including:

- MinRTT scheduling.
- Round-Robin scheduling.
- Rule-based multipath scheduling, where a suitable implementation is available.

The evaluation will consider:

- Video-streaming QoE.
- Rebuffering time.
- Network throughput.
- Packet reordering.
- End-to-end latency.
- Agent convergence and inference overhead.
- Memory and computational overhead.

Experiments will be repeated under different network conditions, with statistical measures used to assess the results.

## 4. Technology Stack

| Component | Technology |
|---|---|
| Operating system | Ubuntu Linux |
| Main programming language | Python 3.12+ |
| Networking implementation | Go |
| Multipath protocol | Go-MPQUIC |
| Reinforcement learning | Soft Actor-Critic |
| Deep learning | PyTorch |
| RL framework | Stable-Baselines3 |
| RL environment | Gymnasium |
| Network emulation | Linux networking tools |
| Data processing | NumPy, Pandas, SciPy |
| Visualization | Matplotlib |
| Video processing | FFmpeg |
| Version control | Git and GitHub |

## 5. System Architecture

The planned system consists of the following components:

```text
             NETWORK TRACE DATASETS
                       |
                       v
              DATA PREPROCESSING
                       |
                       v
                NETWORK TESTBED
                       |
                +------+------+
                |             |
                v             v
              Wi-Fi           LTE
                |             |
                +------+------+
                       |
                       v
                  MPQUIC
                       |
                       v
               NETWORK TELEMETRY
                       |
                       v
                 PYTHON SAC AGENT
                       |
                       v
                SCHEDULING ACTION
                       |
                       v
                MPQUIC SCHEDULER
                       |
                       v
               VIDEO STREAMING
                       |
                       v
              PERFORMANCE REWARD
                       |
                       +------> SAC LEARNING
```

The architecture represents the intended design. The communication interface between the Go-MPQUIC implementation and the Python agent will be developed and tested as part of the implementation.

## 6. Repository Structure

The project repository is organised as follows:

```text
mpquic-sac-video-streaming/
│
├── configs/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── src/
│   ├── agent/
│   ├── environment/
│   └── networking/
│
├── experiments/
│
├── results/
│
├── tests/
│
├── requirements.txt
├── .gitignore
└── README.md
```

External networking dependencies and Python virtual environments are maintained separately from the main repository.

## 7. Installation and Development

### Prerequisites

- Ubuntu Linux.
- Python 3.12 or later.
- Go.
- Git.
- PyTorch.
- Stable-Baselines3.
- Linux networking utilities.

### Clone the repository

```bash
git clone https://github.com/Solomonskywalker/mpquic-sac-video-streaming.git

cd mpquic-sac-video-streaming
```

### Create and activate the virtual environment

```bash
python3.12 -m venv .venv

source .venv/bin/activate
```

### Install Python dependencies

Once `requirements.txt` has been prepared:

```bash
pip install -r requirements.txt
```

### Go-MPQUIC dependency

The project uses the Go-MPQUIC implementation:

https://github.com/qoke/mp-quic-go

The implementation will be maintained separately from the main research repository.

## 8. Development Status

The project is currently in the environment setup and implementation stage.

| Component | Status |
|---|---|
| Ubuntu development environment | Prepared |
| Python virtual environment | Prepared |
| Go environment | Installed |
| GitHub repository | Created |
| MPQUIC implementation | Under investigation |
| MPQUIC client/server testing | Pending |
| Wi-Fi and LTE network emulation | Pending |
| Video streaming server | Pending |
| Network trace preparation | Pending |
| SAC environment | Pending |
| SAC scheduler integration | Pending |
| Model training | Pending |
| Experimental evaluation | Pending |

## 9. Collaboration

Team members can contribute through separate Git branches.

The development workflow is:

1. Clone the repository.
2. Create a branch for the assigned task.
3. Implement and test the changes.
4. Commit the changes with a descriptive message.
5. Push the branch to GitHub.
6. Submit a Pull Request for review.

For example:

```bash
git checkout -b feature/dataset-preprocessing
```

After making changes:

```bash
git add .
git commit -m "Add network trace preprocessing"
git push -u origin feature/dataset-preprocessing
```

The following should not be committed to the repository:

- Python virtual environments.
- Passwords, access tokens or other credentials.
- Large raw datasets.
- Unnecessary model checkpoints.
- Temporary experiment files.

## 10. Research Direction

The main research question is whether a SAC-based traffic scheduler can improve multipath video streaming when network conditions change over time.

The study will investigate how network telemetry can guide traffic distribution across heterogeneous paths and how these decisions affect streaming quality and network performance.

All performance claims will be based on experimental results and comparisons with the selected baseline schedulers.

---

**Repository:** https://github.com/Solomonskywalker/mpquic-sac-video-streaming

**Project:** Deep Reinforcement Learning for Adaptive Multipath QUIC Video Streaming
