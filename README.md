# Reinforcement Learning for Emotion Regulation

This repository contains the code and resources for a project focused on using Reinforcement Learning (RL) to regulate and navigate emotional states based on EEG signals. The project leverages the **DEAP dataset** (Database for Emotion Analysis using Physiological Signals) to map brain activity to the Valence-Arousal (VA) space and trains RL agents to transition between emotional states.

## Repository Structure

- `paper-replication .ipynb`: Jupyter Notebook for replicate the methodology and results of the base paper.
- `paper-inovation.ipynb`: Jupyter Notebook for heuristic approaches to improved the base paper results.
- `rl_emotion_regulation_rl_sachin.pdf`: The main project report containing methodology, and results.
- `Analysis/` & `analysis of results/`: Directories containing the evaluation and visualization of the experimental results.
- `clustering/`: Scripts and data related to the clustering of emotional states in the Valence-Arousal space.
- `output/`: Results of each method and model with each episode

## 🚀 Methodology

The project involves two main components:
1. **Global Emotion Observer (`EEGEmotionNet`)**: A neural network trained on the DEAP dataset to accurately map 32-channel EEG signals to the continuous 2D Valence-Arousal space.

2. **Reinforcement Learning Agents**: RL algorithms are trained to guide a user towards target emotion hee happy state. The following algorithms are implemented and compared:
   - Tabular Q-Learning (`Q-Table`)
   - Deep Q-Network (`DQN`)
   - Double Deep Q-Network (`DDQN`)
   - Expected SARSA

### Reward Shaping & Heuristics
To improve the convergence and success rate of the RL agents, different reward shaping strategies are used:
- **Angular Heuristic**: Penalizes or rewards the agent based on the angular deviation from the target emotion centroid.
- **Distance Heuristic**: Focuses on minimizing the Euclidean distance to the target state in the VA space.

## Technologies Used
- **Python 3**
- **PyTorch** 
- **NumPy & Pandas** 
- **Matplotlib** 
- **DEAP Dataset**
