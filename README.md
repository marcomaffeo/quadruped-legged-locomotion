# Quadruped Legged Locomotion Control

This repository contains a MATLAB-based simulation framework for analyzing and controlling quadruped robot locomotion. The control architecture relies on an optimization-based approach to generate stable walking and running patterns across multiple gaits.

## Control Architecture

The core of the locomotion controller is formulated as a Quadratic Programming (QP) problem, solved efficiently using the `qpSWIFT` solver. The optimization objective is expressed as:

$$ \min \frac{1}{2}x^{\top}Hx+g^{\top}x $$

Subject to the dynamic and physical constraints of the system:
*   Equality constraints: $A_{eq}x=b_{eq}$
*   Inequality constraints: $A_{ineq}x\le b_{ineq}$

This formulation allows the computation of optimal states and ground reaction forces to ensure stable trajectory tracking. 

## Gait Analysis and Parameter Tuning

The project evaluates the quadruped's performance across six distinct gaits. The analysis focuses on how variations in the desired velocity $v_{d}$, robot mass, and friction coefficient $\mu$ impact trajectory tracking, linear and angular velocities, and the z-component of the ground reaction forces:

*   **Trot:** Decreasing the desired velocity primarily reduces the covered distance without significantly affecting the overall tracking performance.
*   **Bound:** Increasing the desired velocity results in a slight improvement in the x-component velocity tracking.
*   **Pacing:** Reducing the robot's mass improves velocity tracking across all components and reduces the overall magnitude of the required ground reaction forces.
*   **Gallop:** Increasing the robot's mass maintains similar tracking capabilities but proportionally increases the magnitude of the dynamic responses and reaction forces.
*   **Trot Run:** Decreasing the friction coefficient causes a more oscillatory trend, which worsens the tracking behavior but reduces the z-component of the ground reaction forces.
*   **Crawl:** Increasing the friction coefficient beyond the unit value demonstrates no significant effect on the robot's overall performance.

## Locomotion Demonstrations

Below are the simulation results demonstrating the quadruped executing the six analyzed gaits.

### 1. Trot

https://github.com/user-attachments/assets/f207eef7-e38f-4a06-b408-bf2fc828a039

### 2. Bound

https://github.com/user-attachments/assets/b564cb49-0153-4ba1-a7e6-139ed2468a15

### 3. Pacing

https://github.com/user-attachments/assets/3db12100-048b-4ced-9ddf-0f944961cef8

### 4. Gallop

https://github.com/user-attachments/assets/97e28413-0015-479c-a0ad-ea644d1dbbba

### 5. Trot Run

https://github.com/user-attachments/assets/86f85f10-a05b-42d1-b3e9-c354d29c2d55

### 6. Crawl

https://github.com/user-attachments/assets/eef4ee4c-a2de-49d5-ad54-07e43b435c7f

## Dependencies

*   MATLAB
*   [qpSWIFT](https://github.com/oxfordcontrol/qpSWIFT) (QP solver for the control allocation)
