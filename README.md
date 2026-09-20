# Multi-Agent Reinforcement Learning for Cooperative Robot Cleaning

A multi-agent reinforcement learning project for cooperative robot cleaning, implementing and evaluating PPO-based methods including **PPO, IPPO, and MAPPO**.

## Overview

This project explores cooperative multi-agent reinforcement learning in a custom grid-based cleaning environment.

Three autonomous agents operate in a **12 × 12 grid world** and must coordinate to clean different types of dirt while avoiding collisions, fragile objects, and safety violations.

The project includes:

- A custom multi-agent environment built with **Gymnasium**
- A PPO training pipeline implemented with **PyTorch**
- Independent Proximal Policy Optimization (**IPPO**)
- Multi-Agent Proximal Policy Optimization (**MAPPO**)
- Fixed and randomized training environments
- Generalisation evaluation on unseen random maps
- Multi-agent behaviour analysis using contribution and policy-diversity metrics

## Environment

| Setting | Value |
|---|---|
| Grid size | 12 × 12 |
| Number of agents | 3 |
| Maximum episode length | 50 steps |
| Action space | Idle, Up, Down, Left, Right |
| Environment modes | Fixed / Random |
| Framework | Gymnasium |

The environment contains normal dirt, large dirt, fragile objects, collision constraints, and a safety mechanism for invalid or unsafe actions.

## Algorithms

### PPO

A PPO training pipeline was implemented from scratch, including:

- Actor and critic neural networks
- Rollout buffers
- Generalized Advantage Estimation (GAE)
- PPO clipped objective
- Entropy regularisation
- Mini-batch optimisation
- Gradient clipping

### IPPO

Independent PPO trains a separate actor and critic for each agent, allowing each robot to learn its own decentralized policy.

### MAPPO

MAPPO uses a **shared actor** together with a **centralized critic**, enabling centralized training while maintaining decentralized agent execution.

## Evaluation

The trained policies were evaluated on unseen randomized environments using several metrics:

- Team return
- Success rate
- Episode length
- Safety violation rate
- Redundant Coverage Ratio (RCR)
- Agent contribution
- Jensen-Shannon Divergence between agent policies

### Example Generalisation Result

For the IPPO model trained in the fixed environment and evaluated on **400 unseen random maps**:

| Metric | Result |
|---|---:|
| Mean team return | 147.815 |
| Mean success rate | 60.2% |
| Safety violation rate | 0.0% |
| Global RCR | 0.095 |

## Tech Stack

- Python
- PyTorch
- Gymnasium
- NumPy
- Matplotlib

## Project Goals

This project investigates how different PPO-based multi-agent reinforcement learning approaches affect:

- Cooperation between agents
- Generalisation to unseen environments
- Policy diversity
- Task efficiency
- Safety and collision avoidance

## Future Work

Planned improvements include:

- More extensive hyperparameter tuning
- Improved reward shaping
- Additional MARL baselines
- Training visualisations
- Animated policy demonstrations
- Larger and more complex environments
