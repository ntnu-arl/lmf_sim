# lmf_sim
This repository contains everything you need to setup the simulator to train and test the navigation methods (ORACLE, A-ORACLE, seVAE-ORACLE) for the LMF drone. It uses the [vcstool](https://github.com/dirk-thomas/vcstool) to specify the repositories and branches to be used.

## Setup

```bash
mkdir -p lmf_sim_ws/src && cd lmf_sim_ws/src
git clone git@github.com:ntnu-arl/lmf_sim.git
vcs import < src/lmf_sim/vcstool/lmf_sim.repos
```

## Build

```bash
cd lmf_sim_ws
catkin config -DCMAKE_BUILD_TYPE=Release
catkin build
```

## Handling of the .repo file

```bash
cd rmf_obelix_ws
vcs export > src/lmf_sim/vcstool/lmf_sim.repos
```