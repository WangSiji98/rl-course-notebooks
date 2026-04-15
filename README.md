# RL Course Notebooks

这是一个按学习顺序整理的强化学习课程 notebook 集合，内容从最基础的表格法一路走到 DQN、Policy Gradient、Actor-Critic、PPO 和连续动作空间入门。

## 课程目录

### 1. 表格法入门
- `rl_q_learning_demo.ipynb`
- `rl_sarsa_demo.ipynb`
- `rl_q_learning_vs_sarsa_demo.ipynb`
- `rl_cliff_walking_demo.ipynb`
- `rl_frozenlake_demo.ipynb`

### 2. DQN 路线
- `rl_dqn_intro_demo.ipynb`
- `rl_dqn_intro_pytorch_demo.ipynb`
- `rl_dqn_replay_target_demo.ipynb`
- `rl_cartpole_dqn_demo.ipynb`
- `rl_cartpole_double_dqn_demo.ipynb`
- `rl_cartpole_dueling_dqn_demo.ipynb`
- `rl_cartpole_prioritized_replay_demo.ipynb`
- `rl_cartpole_rainbow_lite_demo.ipynb`

### 3. 策略梯度 / Actor-Critic 路线
- `rl_cartpole_reinforce_demo.ipynb`
- `rl_cartpole_reinforce_baseline_demo.ipynb`
- `rl_cartpole_actor_critic_demo.ipynb`
- `rl_cartpole_a2c_demo.ipynb`
- `rl_cartpole_ppo_demo.ipynb`

### 4. 连续动作空间入门
- `rl_continuous_action_intro_demo.ipynb`

## 环境准备

推荐直接使用仓库里的 `environment.yml` 创建 conda 环境：

```powershell
conda env create -f environment.yml
conda activate rl-course
python -m ipykernel install --user --name rl-course --display-name "Python (rl-course)"
```

然后启动 Jupyter：

```powershell
jupyter lab
```

如果你只想快速安装核心依赖，也可以手动执行：

```powershell
conda create -n rl-course python=3.10 -y
conda activate rl-course
pip install --extra-index-url https://download.pytorch.org/whl/cu128 torch torchvision torchaudio
pip install gymnasium numpy matplotlib jupyterlab ipykernel
python -m ipykernel install --user --name rl-course --display-name "Python (rl-course)"
```

## GPU 说明

这些 notebook 默认会优先尝试使用 CUDA；如果当前环境的 CUDA / PyTorch / 显卡不兼容，也会自动回退到 CPU。

可以用下面这段代码快速检查 GPU 是否可用：

```python
import torch
print(torch.__version__)
print(torch.cuda.is_available())
print(torch.zeros(1, device="cuda").device if torch.cuda.is_available() else "cpu")
```

## 当前开发环境参考

当前课程编写时使用过的关键版本：

- Python `3.10.20`
- PyTorch `2.11.0+cu128`
- Gymnasium `1.2.3`
- NumPy `2.2.6`
- Matplotlib `3.10.8`

## 使用建议

- 建议按文件名顺序学习，不要一开始就跳到后面的 PPO 或连续动作部分。
- 大部分 notebook 的第一格都会先清理 GPU cache，方便连续学习时减少显存干扰。
- 如果 Jupyter kernel 卡住，直接重启 kernel 通常就够了。

## 仓库目的

这个仓库的目标不是做一个工业级 RL 框架，而是作为一个适合自学、逐步推进的课程型项目。重点在于把每个阶段的核心思想拆开讲清楚。
