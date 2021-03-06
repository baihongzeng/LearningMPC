# LearningMPC
Learning based Model Prodictive Control for online iterative trajectory optimization for F1/10 autonomous racing. The implementation is inspired and based on "Learning How to Autonomously Race a Car:
a Predictive Control Approach, Ugo Rosolia and Francesco Borrelli" 

The car is learning to improve its racing performance iteratively over laps.

Initial Sample Safe Set (Lap 1 and Lap 2) is collected using a path following controller.

Starting from Lap 3, control policies are generated by learning MPC. The MPC enforces the terminal state to be within a convex hull of a selected subset of samples. The sample safe set continously grows as more and more data is being collected along the way. The improvement of racing performance over laps is shown here below.

Lap 5 (Top speed 1.2 m/s)

![](media/lap5.gif)

Lap 25 (Top speed 3 m/s)

![](media/lap25.gif)

After Lap 60, it converges to an optimal policy (Top speed 6 m/s) with precisely controlled high speed drifting.

![](media/lap60_converged_drifting.gif).

With low frictions, it converges to a policy with lower top speed but with more drifting.

![](media/drifting_low_friction.gif).

## Quick Start:

### Install racecar_simulator from:
https://github.com/mlab-upenn/f110-fall2019-skeletons

### The original simulator only accepts *velocity* as control input. We need to make it accept *acceleration* as control input:
Replace the origin `'simulator.cpp'` in `path/racecar_simulator/node` with the `'simulator.cpp'` provided in this repo.

### Replace the track map:
put `.yaml` and `.png` in `/map` into the `/maps` in simulator.
change the map to be launched in `/launch` in simulator.

### Launch simulator:
>roslaunch racecar_simulator simulator.launch

### Repose the car around the start line / finishing line

### Launch the algorithm:
>roslaunch LearningMPC lmpc.launch



