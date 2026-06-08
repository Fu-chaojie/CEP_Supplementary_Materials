# Supplementary-video
Control Engineering Practice 
“Delay-Compensated LPV Model Predictive Control for Trajectory Tracking of Autonomous Vehicles with Steering Actuator Dynamics:
Design and Real-Vehicle Validation on a Steer-by-Wire Platform” Supplementary video
DLC maneuver.mp4 is a video of DLC experiments.
SLC maneuver.mp4 is a video of SLC experiments.
The third-person perspective experimental video.mp4 is from the perspective outside the vehicle.
# Real-Vehicle Experimental Dataset

This repository contains the real-vehicle experimental data used in our paper. All data files are provided in MATLAB `.mat` format. These datasets are utilized to validate and compare the performance of the proposed control algorithm against a baseline under various driving maneuvers.

## 1. Dataset Classification and Description

The data files are categorized by test maneuvers and the applied control algorithms. The specific mappings are as follows:

### 1.1 Single Lane Change (SLC) Maneuver
* **`rec1_552.mat`**: Baseline algorithm data (conventional control without considering the steering system).
* **`rec1_405.mat`**: Experimental data of the proposed control algorithm.
* **`rec1_414.mat`**: Experimental data of the proposed control algorithm.

### 1.2 Double Lane Change (DLC) Maneuver
* **`rec1_555.mat`**: Baseline algorithm data (conventional control without considering the steering system).
* **`rec1_335.mat`**: Experimental data of the proposed control algorithm.

### 1.3 Right-Angle Turn Maneuver
* **`rec1_253.mat`**: Real-vehicle experimental data under the right-angle turn maneuver.

---

## 2. Data Structure and Variable Mapping

All `.mat` files are stored using a unified structure format. Taking `rec1_405` as an example, the locations, physical meanings, and units of the core control and state variables are detailed below:

| Variable | MATLAB Read Path | Unit | Description |
| :--- | :--- | :--- | :--- |
| `t` | `rec1_405.X(2).Data` | `s` | Time stamp |
| `ey` | `rec1_405.Y(25).Data` | `m` | Lateral tracking error |
| `ephi` | `rec1_405.Y(23).Data` | `rad` | Heading error |
| `vx` | `rec1_405.Y(12).Data` | `km/h` | Longitudinal velocity |
| `vy` | `rec1_405.Y(13).Data` | `km/h` | Lateral velocity |
| `ay` | `rec1_405.Y(7).Data` | `g` | Lateral acceleration |

> 📌 **Note:** For additional sensor data or control variables recorded during the experiments, please refer to the variable names and index mappings documented in the **`Path`** field within the corresponding `.mat` file.

---

## 3. MATLAB Code Example

You can use the following brief MATLAB script to load and extract the core data for plotting or further analysis (using `rec1_405` as an example):

```matlab
% Example: Load the proposed algorithm data for the Single Lane Change maneuver
clear; clc;
data = load('rec1_405.mat');

% Extract data
t    = data.rec1_405.X(2).Data;   % Time (s)
ey   = data.rec1_405.Y(25).Data;  % Lateral tracking error (m)
ephi = data.rec1_405.Y(23).Data;  % Heading error (rad)
vx   = data.rec1_405.Y(12).Data;  % Longitudinal velocity (km/h)
vy   = data.rec1_405.Y(13).Data;  % Lateral velocity (km/h)
ay   = data.rec1_405.Y(7).Data;   % Lateral acceleration (g)

% Plot the lateral tracking error as an example
figure;
plot(t, ey, 'LineWidth', 1.5);
grid on;
xlabel('Time (s)');
ylabel('Lateral Error (m)');
title('Single Lane Change - Lateral Tracking Error');
