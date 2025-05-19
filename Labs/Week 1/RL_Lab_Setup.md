
# 🧪 Lab: Reinforcement Learning Environment Setup and Introduction (2 Hours)

## 🎯 Objectives
By the end of this lab, students will be able to:
- Set up a Python environment with Jupyter and Gymnasium
- Understand and interact with Gymnasium environments
- Render Gymnasium environments inside Jupyter
- Write simple RL environment interaction code

---

## 🧰 Prerequisites
- Basic Python knowledge
- Python (3.8+) installed
- Internet connection to install packages

---

## 🛠️ Part 1: Environment Setup (45 minutes)

### ✅ Step 1: Create a Virtual Environment (Optional but Recommended)
```bash
python -m venv rl-env
source rl-env/bin/activate  # On Windows: rl-env\Scripts\activate
```

### ✅ Step 2: Install Required Packages
```bash
pip install jupyter gymnasium[classic-control] numpy matplotlib
```

### ✅ Step 3: Launch Jupyter Notebook
```bash
jupyter notebook
```

Open your browser and navigate to the URL provided in the terminal.

---

## 🧪 Part 2: Introduction to Gymnasium Environments (75 minutes)

### 🔍 Step 1: Create a New Notebook

Create a new Python notebook named `gymnasium_intro.ipynb`.

### ✍️ Step 2: Write and Run the Following Code
```python
import gymnasium as gym
import matplotlib.pyplot as plt
from IPython.display import display, clear_output
import time

# Create the environment with rendering mode for Jupyter
env = gym.make("CartPole-v1", render_mode="rgb_array")
obs, info = env.reset()

for step in range(30):
    img = env.render()

    # Display the image in Jupyter
    plt.imshow(img)
    plt.axis('off')
    clear_output(wait=True)
    display(plt.gcf())
    time.sleep(0.05)

    action = env.action_space.sample()
    obs, reward, terminated, truncated, info = env.step(action)
    done = terminated or truncated
    if done:
        break

env.close()
```

### 🗣️ Step 3: Discussion Points
- What is an **environment**?
- What does `step()` return?
- What does `terminated` vs `truncated` mean?
- How does `render_mode="rgb_array"` work in Gymnasium?
- What is the **action space** and **observation space**?

---

## 📘 Summary
- Installed Gymnasium and Jupyter with rendering support
- Ran and visualized a simple RL simulation
- Understood the basic loop of agent-environment interaction

---

## 🏠 Homework (Optional)
Modify the loop to run an episode until completion and count total rewards.
