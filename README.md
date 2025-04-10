# 🕹️ Deep Q-Learning for Super Mario Bros

A Deep Q-Network (DQN) implementation trained to play **Super Mario Bros** using PyTorch and OpenAI Gym. The agent learns to complete levels using only screen frames as input and reaches consistent flag captures in 2500-4000 episodes.

![Mario Gameplay](gif/mario.gif) 

---

## 🚀 Features

- Dueling DQN architecture
- Frame stacking & frame skipping
- Custom reward function for smarter navigation
- Experience replay with GPU-accelerated sampling
- Epsilon-greedy exploration with adaptive adjustment
- TensorBoard logging for rewards, loss, and epsilon

---

## 🧠 How It Works

The agent observes a stack of 4 grayscale 96x96 frames and selects an action based on Q-values predicted by the DQN. Rewards are shaped to encourage forward progress, efficient movement, and penalize getting stuck or dying. A custom logic handles level transitions and resets tracking when Mario reaches the flag.

**Key tricks:**

- `x_pos - max_x` reward encourages progress without backtracking
- Stuck detection counter resets if Mario hasn’t moved in time
- Level transition resets `max_x` to prevent post-flag death
- Global exploration is re-enabled if new areas are reached after epsilon minimum

---

## 🛠️ Requirements

Tested on:
- Python 3.12.7
- Microsoft C++ Build Tools (Windows SDK, C++ x64/x86 build tools)
- `torch`
- `gym==0.23.1`
- `gym-super-mario-bros==7.4.0`
- `numpy`
- `tensorboard`

Install everything using pip:

```bash
pip install torch numpy gym==0.23.1 gym-super-mario-bros==7.4.0 tensorboard
