
# 🧪 Lab 2: Exploring the Power of Reinforcement Learning with LunarLander (2 Hours)

## 🎯 Objectives
By the end of this lab, students will be able to:
- Interact with a more complex RL environment (`LunarLander-v2`)
- Visualize the environment dynamics
- Understand rewards, actions, and the importance of exploration

---

## 🧰 Prerequisites
- Completion of Lab 1 (Gymnasium setup with Jupyter)
- Gymnasium with Box2D environments installed

---

## 🛠️ Part 1: Setup (15 minutes)

### ✅ Step 1: Install Dependencies (if not done already)
```bash
pip install gymnasium[box2d] matplotlib
```

### ✅ Step 2: Launch Jupyter Notebook
```bash
jupyter notebook
```

---

## 🧪 Part 2: Play with LunarLander-v2 (105 minutes)

### 🔍 Step 1: Create a New Notebook

Create a new Python notebook named `lunarlander_explore.ipynb`.

### ✍️ Step 2: Run This Code to Interact with the Environment
```python
import gymnasium as gym
import matplotlib.pyplot as plt
from IPython.display import display, clear_output
import time

# Create the environment with RGB rendering
env = gym.make("LunarLander-v2", render_mode="rgb_array")
obs, info = env.reset()

total_reward = 0

for step in range(1000):
    img = env.render()

    # Display the rendered image
    plt.imshow(img)
    plt.axis('off')
    clear_output(wait=True)
    display(plt.gcf())
    time.sleep(0.02)

    action = env.action_space.sample()  # Random action
    obs, reward, terminated, truncated, info = env.step(action)
    total_reward += reward
    done = terminated or truncated
    if done:
        break

env.close()
print(f"Total reward: {total_reward}")
```

---

### 🗣️ Discussion Points
- What is the goal in **LunarLander**?
- What are the 4 actions available?
- What does a high or low reward indicate?
- Why does random action fail? (Introduce the idea of policy optimization)

---

## 📘 Summary
- Ran a more visually engaging RL simulation
- Observed how environment dynamics affect performance
- Prepared students to explore learning-based agents in future labs

---

## 🏠 Homework (Optional)
Try using a basic RL agent like `Stable-Baselines3` or write a simple Q-learning update loop to improve the lander’s performance.
