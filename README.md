# Supplementary-Materials
Control Engineering Practice 
"Steering-Lag-Compensated LPV Model Predictive Control for Autonomous Vehicle Trajectory Tracking: Design and Real-Vehicle Validation on a Steer-by-Wire Platform":Supplementary materials
## 1.DLC maneuver.mp4 is a video of DLC experiments.
## 2.SLC maneuver.mp4 is a video of SLC experiments.
## 3.The third-person perspective experimental video.mp4 is from the perspective outside the vehicle.

# Real-Vehicle Experimental Dataset
This repository contains the real-vehicle experimental data used in our paper. All data files are provided in MATLAB `.mat` format. These datasets are utilized to validate and compare the performance of the proposed control algorithm against a baseline under various driving maneuvers.

## 1. Dataset Classification and Description

The data files are categorized by test maneuvers and the applied control algorithms. The specific mappings are as follows:

### 1.1 Single Lane Change (SLC) Maneuver
* **`rec1_552.mat`**: LPV-MPC
* **`rec1_414.mat`**: LC LPV-MPC
* **`rec1_419.mat`**: LC LPV-MPC
* **`rec1_88.mat`**: LQR+FF
* **`rec1_53.mat`**: LQR

### 1.2 Double Lane Change (DLC) Maneuver
* **`rec1_555.mat`**: LPV-MPC
* **`rec1_335.mat`**: LC LPV-MPC
* **`rec1_60.mat`**: LQR+FF
* **`rec1_61.mat`**: LQR

### 1.3 Right-Angle Turn Maneuver
* **`rec1_253.mat`**: LC LPV-MPC
* **`rec1_94.mat`**: LQR+FF
---

## 2. Data Structure and Variable Mapping
The data structures for MPC and LQR are different.


> 📌 **Note:** For additional sensor data or control variables recorded during the experiments, please refer to the variable names and index mappings documented in the **`Path`** field within the corresponding `.mat` file.

---

## 3. MATLAB Code Example

You can use the following brief MATLAB script to load and extract the core data for plotting or further analysis (using `rec1_405` as an example):

```matlab
% Example For MPC Structure

clear; clc;
data = load('rec1_XXX.mat');
% Extract data
t    = data.rec1_XXX.X(2).Data;   % Time (s)
ey   = data.rec1_XXX.Y(25).Data;  % Lateral tracking error (m)
ephi = data.rec1_XXX.Y(23).Data;  % Heading error (rad)
vx   = data.rec1_XXX.Y(12).Data;  % Longitudinal velocity (km/h)
vy   = data.rec1_XXX.Y(13).Data;  % Lateral velocity (km/h)
ay   = data.rec1_XXX.Y(7).Data;   % Lateral acceleration (g)
delta_f   = data.rec1_XXX.Y(11).Data;   % Steering angle (deg)

% Example For LQR Structure
clear; clc;
data = load('rec1_XXX.mat');
t    = data.rec1_XXX.X(2).Data;   % Time (s)
ey   = data.rec1_XXX.Y(3).Data;  % Lateral tracking error (m)
ephi = data.rec1_XXX.Y(2).Data;  % Heading error (rad)
vx   = data.rec1_XXX.Y(8).Data;  % Longitudinal velocity (km/h)
vy   = data.rec1_XXX.Y(9).Data;  % Lateral velocity (km/h)
ay   = data.rec1_XXX.Y(5).Data;   % Lateral acceleration (g)
delta_f   = data.rec1_XXX.Y(7).Data;   % Steering angle (deg)


