# Reinforcement Learning for Emotion Regulation

This repository contains the code and resources for a project focused on using Reinforcement Learning (RL) to regulate and navigate emotional states based on EEG signals. The project leverages the **DEAP dataset** (Database for Emotion Analysis using Physiological Signals) to map brain activity to the Valence-Arousal (VA) space and trains RL agents to transition between emotional states.

## Repository Structure

- `paper-replication .ipynb`: Jupyter Notebook for replicate the methodology and results of the base paper.
- `paper-inovation.ipynb`: Jupyter Notebook for heuristic approaches to improved the base paper results.
- `rl_emotion_regulation_rl_sachin.pdf`: The main project report containing methodology, and results.
- `analysis of results/`: Directories containing the evaluation and visualization of the experimental results.
- `clustering/`: Scripts and data related to the clustering of emotional states in the Valence-Arousal space.
- `output/`: Results of each method and model with each episode

## Methodology

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

## Dataset

The project relies on the **DEAP Dataset** (Database for Emotion Analysis using Physiological Signals), which is a widely recognized multimodal dataset for the analysis of human affective states.

*   **Content:** The dataset contains EEG and peripheral physiological signals of 32 participants who watched 40 one-minute music videos.
*   **Labels:** Each video was rated by participants in terms of arousal, valence, like/dislike, dominance, and familiarity.
*   **Relevance:** In this project, the 32-channel EEG signals are used to map brain activity to the continuous 2D Valence-Arousal (VA) space, which serves as the environment for our Reinforcement Learning agents.

You can find and download the preprocessed dataset from Kaggle:
[DEAP Dataset on Kaggle](https://www.kaggle.com/datasets/manh123df/deap-dataset)

## Cloning Strategy and Environment Setup

To get a local copy up and running, it is recommended to use an isolated Python environment. Follow these steps:

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Prit210/rl-poject.git
   cd rl-poject
   ```

2. **Create a Virtual Environment (Optional but Recommended):**
   Using `venv`:
   ```bash
   python -m venv venv
   # On Windows:
   venv\Scripts\activate
   # On macOS/Linux:
   source venv/bin/activate
   ```
   Or using Conda:
   ```bash
   conda create -n rl_emotion python=3.9
   conda activate rl_emotion
   ```

##  How to Run

1. **Install Dependencies:**
   Ensure you have your virtual environment activated, then install the required libraries:
   ```bash
   pip install torch numpy pandas matplotlib jupyterlab
   ```

2. **Dataset Setup:** 
   - Download the DEAP dataset archive from the [Kaggle link](https://www.kaggle.com/datasets/manh123df/deap-dataset).
   - Extract the contents of the zip file.
   - You should see `.dat` files for each of the 32 participants (e.g., `s01.dat`, `s02.dat`, etc.).
   - Place these files in a designated data folder within your project directory. *(Note: Check the early cells of the Jupyter Notebooks to see the exact expected path, e.g., `data/` or similar, and adjust if necessary.)*

3. **Running the Experiments:**
   - Launch the Jupyter environment from the project root:
     ```bash
     jupyter notebook
     ```
   - **`paper-replication.ipynb`**: Open this notebook to understand the baseline methodology. Run all cells to initialize the `EEGEmotionNet`, process the DEAP data, and train the baseline RL algorithms.
   - **`paper-inovation.ipynb`**: Open this notebook to test the proposed improvements. It contains advanced RL algorithms (DQN, DDQN, Expected SARSA) and heuristic reward shaping (Angular and Distance heuristics).
   
4. **Evaluating Results:**
   - Once the notebooks finish executing, check the `output/` and `Analysis/` directories.
   - The notebooks will generate loss curves, reward plots, and path visualizations detailing how the RL agent transitions from an initial emotional state to the target state in the Valence-Arousal space.
