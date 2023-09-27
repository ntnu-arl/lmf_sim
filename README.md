# lmf_sim
This repository contains everything you need to setup the simulator to train and test the navigation methods (ORACLE, A-ORACLE, seVAE-ORACLE) for the LMF drone. It uses the [vcstool](https://github.com/dirk-thomas/vcstool) to specify the repositories and branches to be used.

## Setup

```bash
mkdir -p lmf_sim_ws/src && cd lmf_sim_ws/src
git clone git@github.com:ntnu-arl/lmf_sim.git
```

If traning/testing ORACLE
```bash
vcs import < src/lmf_sim/vcstool/lmf_sim.repos # ROS Melodic + OpenCV 3
vcs import < src/lmf_sim/vcstool/lmf_sim_noetic.repos # ROS Noetic + OpenCV 4
```

If traning/testing A-ORACLE
```bash
vcs import < src/lmf_sim/vcstool/lmf_sim_attentive.repos # ROS Melodic + OpenCV 3
vcs import < src/lmf_sim/vcstool/lmf_sim_attentive_noetic.repos # ROS Noetic + OpenCV 4
cd src/perception/visual_saliency_ros
git submodule update --init --recursive
cd src/perception/darknet_ros
git submodule update --init --recursive
```

If traning/testing seVAE-ORACLE
```bash
vcs import < src/lmf_sim/vcstool/lmf_sim_sevae.repos # ROS Melodic + OpenCV 3
vcs import < src/lmf_sim/vcstool/lmf_sim_sevae_noetic.repos # ROS Noetic + OpenCV 4
```

## Build

```bash
sudo apt-get install ros-${ROS_DISTRO}-octomap-msgs ros-${ROS_DISTRO}-octomap-ros
cd lmf_sim_ws
catkin config -DCMAKE_BUILD_TYPE=Release --blacklist deep_collision_predictor rotors_hil_interface
catkin build
```

## Handling of the .repo files

```bash
cd lmf_sim_ws
vcs export > src/lmf_sim/vcstool/FILE_NAME.repos
```
