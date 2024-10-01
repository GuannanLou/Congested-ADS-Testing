# Autonomous Driving System Testing: Traffic Density Does Matter

This repository contains the code for the paper： *Autonomous Driving System Testing: Traffic
Density Does Matter*.

## Setup

Download and setup CARLA 0.9.10.1

```
mkdir carla
cd carla
wget https://carla-releases.s3.eu-west-3.amazonaws.com/Linux/CARLA_0.9.10.1.tar.gz
wget https://carla-releases.s3.eu-west-3.amazonaws.com/Linux/AdditionalMaps_0.9.10.1.tar.gz
tar -xf CARLA_0.9.10.1.tar.gz
tar -xf AdditionalMaps_0.9.10.1.tar.gz
rm CARLA_0.9.10.1.tar.gz
rm AdditionalMaps_0.9.10.1.tar.gz
cd ..
```

Clone this repo and build the environment

```
git clone https://github.com/OpenPerceptionX/TCP.git
cd TCP
conda env create -f environment.yml --name TCP
conda activate TCP
```

```
export PYTHONPATH=$PYTHONPATH:PATH_TO_TCP
```

## Result

Download our dataset through [GoogleDrive](). The total size of our dataset is aroung 135G, make sure you have enough space.

## Evaluation

First, launch the carla server,

```
cd CARLA_ROOT
./CarlaUE4.sh --world-port=2000 -opengl
```

Set the carla path, routes file, scenario file, model ckpt, and data path for evaluation in ``leaderboard/scripts/run_evaluation.sh``.

Start the evaluation

```
sh leaderboard/scripts/run_evaluation.sh
```

## Citation

Waiting for proceeding

## License

All code within this repository is under [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).

## Acknowledgements

Our code is based on several repositories:

- [TCP](https://github.com/OpenDriveLab/TCP)
- [InterFuser](https://github.com/opendilab/InterFuser)
- [CARLA Leaderboard](https://github.com/carla-simulator/leaderboard)
- [Scenario Runner](https://github.com/carla-simulator/scenario_runner)
- [Roach](https://github.com/zhejz/carla-roach)
