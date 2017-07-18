[//]: # (Image References)

[image0]: Equations.png "Equations"
[image1]: Transformation.png "Transformations"


# CarND-Controls-MPC
Self-Driving Car Engineer Nanodegree Program

---

## Student describes their model in detail. This includes the state, actuators and update equations.

The model used is a kinematic one based on this equations:

![Equations][image0]

* [x,y,ψ,v] is the state of the vehicle in time t and t+1
* Lf is a physical characteristic of the vehicle, which measures the distance between the front of the vehicle and its center of gravity. The larger the vehicle , the slower the turn rate.
* [δ,a] are the actuators or control inputs, to our system. Delta for steering angle and "a" for acceleration (positive or negative-braking) 


## Student discusses the reasoning behind the chosen N (timestep length) and dt (elapsed duration between timesteps) values. Additionally the student details the previous values tried.

As mentioned in the lessons, a good approach to setting N, dt, and T is to first determine a reasonable range for T and then tune dt and N appropriately, keeping the effect of each in mind.

First I used the standard values N= 10 and dt=0.1, T= 1 second, but after increasing the reference speed to 100 mph it seems convenient to increase N to maintain the distance ahead the vehicle is considering. N is the determinant of the number of variables the optimized by MPC and as consequence the major driver of computational cost, but after testing it, there is no penalization.


## Polynomial Fitting and MPC Preprocessing: If the student preprocesses waypoints, the vehicle state, and/or actuators prior to the MPC procedure it is described.

* As recommended, waypoints are transformed to the vehicle's coordinate system with the convention that the heading of the vehicle system is towards the x-axis, and the starting point in the coordinate system is (0,0) and angle = 0º. This simplifies the calculation of the cross-track error and the orientation error.

![Transformations][image1]

## Model Predictive Control with Latency

The latency is taken into account using the kinematic model equations, to simulate the state of the vehicle in 100 ms: 

* double pred_x   = v * latency;
* double pred_y   = 0;
*... 
* so the new state is: state << pred_x, pred_y, pred_psi, pred_v, pred_cte, pred_epsi;

