[//]: # (Image References)

[image0]: ../term2/CarND-MPC-Project-master/Equations.png "Equations"
[image1]: ./../master/tools/initial_position.png "waypoint_rotation.png"


# CarND-Controls-MPC
Self-Driving Car Engineer Nanodegree Program

---

## Student describes their model in detail. This includes the state, actuators and update equations.

The model used is a kinematic one based on this equations:

![Equations][image0]

[x,y,ψ,v] is the state of the vehicle, Lf is a physical characteristic of the vehicle, and [δ,a] are the actuators, or control inputs, to our system.


## Student discusses the reasoning behind the chosen N (timestep length) and dt (elapsed duration between timesteps) values. Additionally the student details the previous values tried.


1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./mpc`.

## Polynomial Fitting and MPC Preprocessing

1. It's recommended to test the MPC on basic examples to see if your implementation behaves as desired. One possible example
is the vehicle starting offset of a straight line (reference). If the MPC implementation is correct, after some number of timesteps
(not too many) it should find and track the reference line.
2. The `lake_track_waypoints.csv` file has the waypoints of the lake track. You could use this to fit polynomials and points and see of how well your model tracks curve. NOTE: This file might be not completely in sync with the simulator so your solution should NOT depend on it.
3. For visualization this C++ [matplotlib wrapper](https://github.com/lava/matplotlib-cpp) could be helpful.

## Model Predictive Control with Latency

