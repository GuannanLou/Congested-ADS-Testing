# Autonomous Driving System Testing: Traffic Density Does Matter

This repository contains the implementation for the paper:

> **Autonomous Driving System Testing: Traffic Density Does Matter**

---

# Setup

## 1. Download and Setup CARLA 0.9.10.1

We recommend placing CARLA outside this repository.

Example directory structure:

```text
~/Projects/
├── CARLA_0.9.10/
└── Congested-Scenario-Testing-main/
```

Install CARLA:

```bash
cd ~/Projects

mkdir CARLA_0.9.10
cd CARLA_0.9.10

wget https://carla-releases.s3.eu-west-3.amazonaws.com/Linux/CARLA_0.9.10.1.tar.gz
wget https://carla-releases.s3.eu-west-3.amazonaws.com/Linux/AdditionalMaps_0.9.10.1.tar.gz

tar -xf CARLA_0.9.10.1.tar.gz
tar -xf AdditionalMaps_0.9.10.1.tar.gz

rm CARLA_0.9.10.1.tar.gz
rm AdditionalMaps_0.9.10.1.tar.gz
```

---

## 2. Clone This Repository and Build the Environment

```bash
cd ~/Projects

git clone https://github.com/OpenPerceptionX/TCP.git Congested-Scenario-Testing-main

cd Congested-Scenario-Testing-main

conda env create -f environment.yml --name TCP
conda activate TCP
```

---

# Directory Structure

The recommended project structure is:

```text
~/Projects/
├── CARLA_0.9.10/
│   ├── CarlaUE4.sh
│   └── PythonAPI/
│
├── Congested-Scenario-Testing-main/
│   ├── experiment_config.sh
│   ├── leaderboard/
│   ├── scenario_runner/
│   ├── team_code/
│   ├── TCP/
│   └── leaderboard/scripts/
│
└── IMGDATA/
```

Directory descriptions:

- `CARLA_0.9.10/`
  - CARLA simulator root directory.

- `Congested-Scenario-Testing-main/`
  - Main project repository.

- `IMGDATA/`
  - Stores collected images, logs, fitness files, and experiment outputs.

---

# Configuration

Before running experiments, modify:

```bash
~/Projects/Congested-Scenario-Testing-main/experiment_config.sh
```

Example configuration:

```bash
#!/usr/bin/env bash

export CARLA_ROOT="$HOME/Projects/CARLA_0.9.10"
export IMGDATA_ROOT="$HOME/Projects/IMGDATA"

export PORT=2000
export TM_PORT=2500
export TIMEOUT=120

export SAVE_IMG=True
export LOG=False
export DATA_COLLECTION=True
export MAX_SPEED=5

export RECORD_PATH=""
```

Main configuration items:

| Variable | Description |
|---|---|
| `CARLA_ROOT` | Path to CARLA |
| `IMGDATA_ROOT` | Output data directory |
| `PORT` | CARLA server port |
| `TM_PORT` | Traffic Manager port |
| `TIMEOUT` | Timeout for one experiment |
| `SAVE_IMG` | Whether to save images |

---

# Evaluation

Activate the environment first:

```bash
conda activate TCP
```

Run the full experiment pipeline:

```bash
cd ~/Projects/Congested-Scenario-Testing-main

python leaderboard/scripts/pipline.py
```

The pipeline automatically:

1. launches CARLA,
2. runs ADS evaluation,
3. tests different traffic density levels,
4. saves experiment outputs to `IMGDATA_ROOT`.

---

# Single Experiment Execution

A single evaluation case can be launched using:

```bash
bash leaderboard/scripts/test_basement.sh <MODEL> <SECTION> <LEVEL>
```

Example:

```bash
bash leaderboard/scripts/test_basement.sh TCP Curve 0

bash leaderboard/scripts/test_basement.sh InterFuser Straight 4
```

Arguments:

| Argument | Options |
|---|---|
| `MODEL` | `TCP`, `InterFuser` |
| `SECTION` | `Curve`, `Straight` |
| `LEVEL` | `0`, `1`, `2`, `3`, `4`, `baseline` |

---

# Results

Download our dataset through Google Drive.

The dataset size is approximately **135 GB**, so please ensure sufficient disk space before downloading.

---

# Citation

Waiting for proceeding.

---

# License

All code within this repository is under:

[Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0)

---

# Acknowledgements

This project is based on several excellent repositories:

- TCP  
  https://github.com/OpenDriveLab/TCP

- InterFuser  
  https://github.com/opendilab/InterFuser

- CARLA Leaderboard  
  https://github.com/carla-simulator/leaderboard

- Scenario Runner  
  https://github.com/carla-simulator/scenario_runner

- Roach  
  https://github.com/zhejz/carla-roach
