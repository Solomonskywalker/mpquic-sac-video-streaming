# Deep Reinforcement Learning for Adaptive Multipath QUIC Video Streaming

**Using Soft Actor-Critic (SAC) for Adaptive Traffic Scheduling over Heterogeneous Network Paths**

---

## Project Overview

This project investigates the application of Deep Reinforcement Learning (DRL) to adaptive multipath video streaming using Multipath QUIC (MPQUIC).

The main objective is to develop a **Soft Actor-Critic (SAC)** agent capable of making adaptive traffic-scheduling decisions across heterogeneous network paths, such as Wi-Fi and LTE/4G/5G.

By observing network conditions and MPQUIC telemetry, the proposed agent will learn scheduling policies that aim to improve video-streaming Quality of Experience (QoE), reduce rebuffering time, optimize throughput, and minimize packet reordering.

The research focuses on integrating reinforcement learning with real-time multipath network behavior.

## Research Objectives

The primary objectives are:

1. Develop an adaptive multipath traffic-scheduling mechanism using SAC.
2. Investigate the use of MPQUIC telemetry for reinforcement-learning observations.
3. Design a continuous action space suitable for adaptive multipath scheduling.
4. Evaluate performance under changing heterogeneous network conditions.
5. Compare the proposed SAC scheduler against conventional multipath scheduling strategies.
6. Analyze the impact of adaptive scheduling on video-streaming QoE.

## Proposed Methodology

The project follows a reinforcement-learning-based networking approach.

### 1. Network Environment

Establish an MPQUIC testbed with multiple network paths representing heterogeneous connections, such as Wi-Fi and LTE.

Network conditions will be varied using real-world bandwidth traces and controlled network emulation.

### 2. Dataset Preparation

Publicly available mobile-network and bandwidth traces will be investigated and prepared for experimental use.

The preparation process will include:

- Dataset inspection and validation.
- Handling missing or invalid measurements.
- Timestamp and measurement normalization.
- Trace visualization.
- Conversion into a format suitable for network-condition replay.

### 3. Reinforcement Learning Agent

The proposed agent will use **Soft Actor-Critic (SAC)**.

The agent will interact with the networking environment through:

- **Observations:** network telemetry, including bandwidth, RTT, packet loss, and other available path statistics.
- **Actions:** continuous scheduling decisions that influence traffic distribution across available paths.
- **Rewards:** feedback based on throughput, rebuffering, packet reordering, and streaming QoE.

The agent will learn through repeated interaction with the network environment.

### 4. Experimental Evaluation

The proposed scheduler will be evaluated against conventional multipath scheduling baselines.

The evaluation will investigate:

- Video-streaming QoE.
- Rebuffering time.
- Network throughput.
- Packet reordering.
- End-to-end latency.
- Agent convergence and inference overhead.
- Memory and computational overhead.

Repeated experiments and statistical validation will be used to assess performance.

## Technology Stack

| Component | Technology |
|---|---|
| Main programming language | Python |
| Networking implementation | Go |
| Reinforcement learning | Soft Actor-Critic (SAC) |
| Deep learning framework | PyTorch |
| RL framework | Stable-Baselines3 |
| Networking protocol | Multipath QUIC |
| Networking testbed | Go-MPQUIC |
| Network emulation | Linux networking tools |
| Data processing | NumPy, Pandas, SciPy |
| Visualization | Matplotlib |
| Version control | Git and GitHub |

## Proposed Architecture

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
                 MPQUIC LAYER
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
                       +----> SAC LEARNING
```

*Note: This is the proposed architecture. The exact integration interface between Go-MPQUIC and the Python SAC agent will be determined during implementation.*

## Project Structure

The planned repository structure is:

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

External networking dependencies and local virtual environments will be maintained separately from the main research repository.

## Installation and Development

### Prerequisites

- Ubuntu Linux
- Python 3.12+
- Go 1.26+
- Git
- PyTorch
- Stable-Baselines3
- Linux networking utilities

### Clone the repository

```bash
git clone https://github.com/Solomonskywalker/mpquic-sac-video-streaming.git
cd mpquic-sac-video-streaming
```

### Create a Python virtual environment

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### Install Python dependencies

Once the project dependency file is prepared:

```bash
pip install -r requirements.txt
```

### Networking dependency

The project currently investigates the Go-MPQUIC implementation:

https://github.com/qoke/mp-quic-go

It will be maintained as an external dependency rather than copied into this repository.

## Collaboration

We welcome collaboration among project team members.

### Development workflow

1. Clone the project repository.
2. Create a separate branch for your task.
3. Implement and test your changes.
4. Commit your work with a descriptive commit message.
5. Push your branch to GitHub.
6. Open a Pull Request for review.

Example:

```bash
git checkout -b feature/dataset-preprocessing
```

After making changes:

```bash
git add .
git commit -m "Add network trace preprocessing"
git push -u origin feature/dataset-preprocessing
```

Please avoid committing:

- Virtual environments.
- Personal access tokens or passwords.
- Raw datasets and large binary files.
- Unnecessary model checkpoints.
- Temporary experiment files.

## Current Development Status

This project is under active development.

| Component | Status |
|---|---|
| Python environment | Prepared |
| PyTorch and Stable-Baselines3 | Installed |
| Go environment | Installed |
| GitHub repository | Created |
| MPQUIC implementation investigation | In progress |
| MPQUIC build and testing | Pending |
| Dataset selection | Pending |
| Dataset preprocessing | Pending |
| Network emulation | Pending |
| SAC environment development | Pending |
| SAC scheduler integration | Pending |
| Model training | Pending |
| Experimental evaluation | Pending |

## Research Direction

The central research direction is to investigate whether a continuous-action SAC agent can learn effective adaptive traffic-scheduling policies using MPQUIC network telemetry under heterogeneous and dynamically changing network conditions.

The implementation and experimental results will be used to assess the effectiveness of the proposed approach.

## Team

**Research project:** Deep Reinforcement Learning for Adaptive Multipath QUIC Video Streaming

**Repository:** [mpquic-sac-video-streaming](https://github.com/Solomonskywalker/mpquic-sac-video-streaming)

Team members and individual contributions will be documented as development progresses.

---

**Note:** This repository is intended for academic research and experimentation. Research findings and performance claims will be added after experimental validation.
