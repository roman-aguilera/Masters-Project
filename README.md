# Masters-Project: High Dimaneionality, Value Iteration, and Barycentric Interpolation in Robotic Control
Materials from my masters project at UCSB, "High Dimaneionality, Value Iteration, and Barycentric Interpolation in Robotic Control". 

# Robotic Control with Value Iteration and Barycentric Interpolation

## Motivation & Problem Statement

This project addresses the challenge of designing controllers for high-dimensional robotic systems while ensuring computational tractability. Discretizing the robot’s state space (e.g., a 3-link robotic arm) leads to an exponential increase in possible states, making brute-force methods impractical due to memory and time constraints.

## Key Methods

### 1. Value Iteration Algorithm

A classic dynamic programming method used to find optimal policies by iteratively updating value functions until convergence. The project explores its application in discrete and continuous control scenarios.

### 2. Gridworld Example

A simplified 2D environment to illustrate value iteration.

- **Actions:** up, down, left, right, and diagonals.
- **Initial setup:** goal state value = 1; all other states = -1000.
- **Outcome:** convergence showed how a policy can guide any starting position to the goal.

**Modified Gridworld:**

- Actions scaled by 0.5, leading to non-integer transitions.
- **Issue:** information about the goal state did not fully propagate due to reliance on the nearest neighbor approach.

### 3. Barycentric Interpolation

Introduced to address limitations in the modified Gridworld.

- After a non-integer state transition, the new state's value is interpolated from surrounding mesh points using weighted sums.
- Solved as a linear inverse problem to compute interpolation weights.
- **Result:** ensured smooth value propagation across the grid, improving policy performance.

### 4. Double Integrator Example

- **Task:** move a cart to zero position and velocity using acceleration control.
- **Continuous-time optimal policy:** accelerate halfway, then decelerate.
- **Observation:** discretization altered the problem, resulting in different trajectories.
- Used value iteration and barycentric interpolation to derive feasible policies.
- Noted non-smooth behavior near the goal due to discretization effects.

## Code Optimizations

- Precomputed nearest neighbors and barycentric weights to speed up value updates.
- Used MATLAB's vectorized operations and mesh generation (`ndgrid`) to replace nested loops.
- Enabled evaluating all state-action transitions simultaneously, greatly improving computational efficiency.

## Conclusion
The project successfully explores the combination of value iteration and barycentric interpolation for handling high-dimensional robotic control problems, offering insights into practical challenges like state space discretization and efficient policy computation.
