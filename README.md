

<div align="center">
<img src=image/logo1.png width=70% />
</div>

<h1 align="center"> MARLlib: The MARL Extension for RLlib </h1>

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)]()

**Multi-Agent RLlib (MARLlib)** is ***a comprehensive Multi-Agent Reinforcement Learning algorithm library*** based on [**Ray**](https://github.com/ray-project/ray) and one of its toolkits [**RLlib**](https://github.com/ray-project/ray/tree/master/rllib). It provides MARL research community with a unified platform for building, training, and evaluating MARL algorithms.

There are four core features of **MARLlib**.

- It unifies diverse algorithm pipeline with a newly proposed agent-level distributed dataflow. Currently, MARLlib delivers 18 algorithms and is able to handle cooperative (team-reward-only cooperation), collaborative (individual-reward-accessible cooperation), competitive (individual competition), and mixed (teamwork-based competition) tasks.
- It unifies multi-agent environment interfaces with a new interface following Gym standard and supports both synchronous and asynchronous agent-environment interaction. Currently, MARLlib provides support to ten environments.
- It provides three parameter sharing strategies, namely full-sharing, non-sharing, and group-sharing, by implementing the policy mapping API of RLlib. This is implemented to be fully decoupled from algorithms and environments, and is completely controlled by configuration files.
- It provides standard 2 or 20 millions timesteps learning curve in the form of CSV of each task-algorithm for reference. These results are reproducible as configuration files for each experiment are provided along. In total, more than a thousand experiments are conducted and released. 

<div align="center">
<img src=image/overview.png width=100% />
</div>


## Overview

### Environments

Most of the popular environments in MARL research are supported by MARLlib:

| Env Name | Learning Mode | Observability | Action Space | Observations |
| ----------- | ----------- | ----------- | ----------- | ----------- |
| [LBF](https://github.com/semitable/lb-foraging)  | cooperative + collaborative | Both | Discrete | Discrete  |
| [RWARE](https://github.com/semitable/robotic-warehouse)  | cooperative | Partial | Discrete | Discrete  |
| [MPE](https://github.com/openai/multiagent-particle-envs)  | cooperative + collaborative + mixed | Both | Both | Continuous  |
| [SMAC](https://github.com/oxwhirl/smac)  | cooperative | Partial | Discrete | Continuous |
| [MetaDrive](https://github.com/decisionforce/metadrive)  | collaborative | Partial | Continuous | Continuous |
|[MAgent](https://www.pettingzoo.ml/magent) | collaborative + mixed | Partial | Discrete | Discrete |
| [Pommerman](https://github.com/MultiAgentLearning/playground)  | collaborative + competitive + mixed | Both | Discrete | Discrete |
| [MAMuJoCo](https://github.com/schroederdewitt/multiagent_mujoco)  | cooperative | Partial | Continuous | Continuous |
| [GRF](https://github.com/google-research/football)  | collaborative + mixed | Full | Discrete | Continuous |
| [Hanabi](https://github.com/deepmind/hanabi-learning-environment) | cooperative | Partial | Discrete | Discrete |

Each environment has a readme file, standing as the instruction for this task, talking about env settings, installation, and some important notes.


### Algorithms

We provide three types of MARL algorithms as our baselines including:

**Independent Learning:** 
IQL
DDPG
PG
A2C
TRPO
PPO

**Centralized Critic:**
COMA 
MADDPG 
MAAC 
MAPPO
MATRPO
HATRPO
HAPPO

**Value Decomposition:**
VDN
QMIX
FACMAC
VDAC
VDPPO

Here is a chart describing the characteristics of each algorithm:

| Algorithm                                                    | Support Task Mode | Need Central Information | Discrete Action   | Continuous Action | Learning Categorize        | Type       |
| ------------------------------------------------------------ | ----------------- | ----------------- | ---------- | -------------------- | ---------- | ---------- |
| IQL*                                                         | cooperative collaborative competitive mixed             |                 | :heavy_check_mark:   |    | Independent Learning | Off Policy |
| [PG](https://papers.nips.cc/paper/1713-policy-gradient-methods-for-reinforcement-learning-with-function-approximation.pdf) | cooperative collaborative competitive mixed             |                 | :heavy_check_mark:       | :heavy_check_mark:   | Independent Learning | On Policy  |
| [A2C](https://arxiv.org/abs/1602.01783)                      | cooperative collaborative competitive mixed             |                 | :heavy_check_mark:       | :heavy_check_mark:   | Independent Learning | On Policy  |
| [DDPG](https://arxiv.org/abs/1509.02971)                     | cooperative collaborative competitive mixed             |                 |  | :heavy_check_mark:   | Independent Learning | Off Policy |
| [TRPO](http://proceedings.mlr.press/v37/schulman15.pdf)      | cooperative collaborative competitive mixed             |                 | :heavy_check_mark:       | :heavy_check_mark:   | Independent Learning | On Policy  |
| [PPO](https://arxiv.org/abs/1707.06347)                      | cooperative collaborative competitive mixed             |                 | :heavy_check_mark:       | :heavy_check_mark:   | Independent Learning | On Policy  |
| [COMA](https://ojs.aaai.org/index.php/AAAI/article/download/11794/11653) | cooperative collaborative competitive mixed              | :heavy_check_mark:               | :heavy_check_mark:       |   | Centralized Critic   | On Policy  |
| [MADDPG](https://arxiv.org/abs/1706.02275)                   | cooperative collaborative competitive mixed             | :heavy_check_mark:               |  | :heavy_check_mark:   | Centralized Critic   | Off Policy |
| MAA2C*                                                       | cooperative collaborative competitive mixed             | :heavy_check_mark:               | :heavy_check_mark:       | :heavy_check_mark:   | Centralized Critic   | On Policy  |
| MATRPO*                                                      | cooperative collaborative competitive mixed             | :heavy_check_mark:               | :heavy_check_mark:       | :heavy_check_mark:   | Centralized Critic   | On Policy  |
| [MAPPO](https://arxiv.org/abs/2103.01955)                    | cooperative collaborative competitive mixed             | :heavy_check_mark:               | :heavy_check_mark:       | :heavy_check_mark:   | Centralized Critic   | On Policy  |
| [HATRPO](https://arxiv.org/abs/2109.11251)                   | Cooperative       | :heavy_check_mark:               | :heavy_check_mark:       | :heavy_check_mark:   | Centralized Critic   | On Policy  |
| [HAPPO](https://arxiv.org/abs/2109.11251)                    | Cooperative       | :heavy_check_mark:               | :heavy_check_mark:       | :heavy_check_mark:   | Centralized Critic   | On Policy  |
| [VDN](https://arxiv.org/abs/1706.05296)                      | Cooperative       |                 | :heavy_check_mark:   |    | Value Decomposition  | Off Policy |
| [QMIX](https://arxiv.org/abs/1803.11485)                     | Cooperative       | :heavy_check_mark:               | :heavy_check_mark:   |   | Value Decomposition  | Off Policy |
| [FACMAC](https://arxiv.org/abs/2003.06709)                   | Cooperative       | :heavy_check_mark:               |  | :heavy_check_mark:   | Value Decomposition  | Off Policy |
| [VDAC](https://arxiv.org/abs/2007.12306)                     | Cooperative       | :heavy_check_mark:               | :heavy_check_mark:       | :heavy_check_mark:   | Value Decomposition  | On Policy  |
| VDPPO*                                                       | Cooperative       | :heavy_check_mark:               | :heavy_check_mark:       | :heavy_check_mark:   | Value Decomposition  | On Policy  |

*IQL* is the multi-agent version of Q learning.
*MAA2C* and *MATRPO* are the centralized version of A2C and TRPO.
*VDPPO* is the value decomposition version of PPO.



### Environment-Algorithm Combination

Y for available, N for not suitable, P for partially available on some scenarios.
(Note: in our code, independent algorithms may not have **I** as prefix. For instance, PPO = IPPO)

| Env w Algorithm | IQL  | PG   | A2C  | DDPG | TRPO | PPO  | COMA | MADDPG | MAAC | MATRPO | MAPPO | HATRPO | HAPPO | VDN  | QMIX | FACMAC | VDAC | VDPPO |
| --------------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ------ | ---- | ------ | ----- | ------ | ----- | ---- | ---- | ------ | ---- | ----- |
| LBF             | Y    | Y    | Y    | N    | Y    | Y    | Y    | N      | Y    | Y      | Y     | Y      | Y     | P    | P    | P      | P    | P     |
| RWARE           | Y    | Y    | Y    | N    | Y    | Y    | Y    | N      | Y    | Y      | Y     | Y      | Y     | Y    | Y    | Y      | Y    | Y     |
| MPE             | P    | Y    | Y    | P    | Y    | Y    | P    | P      | Y    | Y      | Y     | Y      | Y     | Y    | Y    | Y      | Y    | Y     |
| SMAC            | Y    | Y    | Y    | N    | Y    | Y    | Y    | N      | Y    | Y      | Y     | Y      | Y     | Y    | Y    | Y      | Y    | Y     |
| MetaDrive       | N    | Y    | Y    | Y    | Y    | Y    | N    | N      | N    | N      | N     | N      | N     | N    | N    | N      | N    | N     |
| MAgent          | Y    | Y    | Y    | N    | Y    | Y    | Y    | N      | Y    | Y      | Y     | Y      | Y     | N    | N    | N      | N    | N     |
| Pommerman       | Y    | Y    | Y    | N    | Y    | Y    | P    | N      | Y    | Y      | Y     | Y      | Y     | P    | P    | P      | P    | P     |
| MAMuJoCo        | N    | Y    | Y    | Y    | Y    | Y    | N    | Y      | Y    | Y      | Y     | Y      | Y     | N    | N    | Y      | Y    | Y     |
| GRF             | Y    | Y    | Y    | N    | Y    | Y    | Y    | N      | Y    | Y      | Y     | Y      | Y     | Y    | Y    | Y      | Y    | Y     |
| Hanabi          | Y    | Y    | Y    | N    | Y    | Y    | Y    | N      | Y    | Y      | Y     | Y      | Y     | N    | N    | N      | N    | N     |

You can find a comprehensive list of existing MARL algorithms in different environments  [here](https://github.com/ICLR2023Paper4242/MARLlib/tree/main/envs).



### Why MARLlib?

Here we provide a table for the comparison of MARLlib and existing work.

|   Library   | Github Stars | Task Mode | Supported Env | Algorithm | Parameter Sharing  | Asynchronous Interact | Framework
|:-------------:|:-------------:|:-------------:|:-------------:|:--------------:|:----------------:|:-----------------:|:---------------------:
|     [PyMARL](https://github.com/oxwhirl/pymarl) | [![GitHub stars](https://img.shields.io/github/stars/oxwhirl/pymarl)](https://github.com/oxwhirl/pymarl/stargazers)    |       cooperative      |       1       |       Independent Learning(1) + Centralized Critic(1) + Value Decomposition(3)       |         full-sharing        |                   | *
|    [PyMARL2](https://github.com/hijkzzz/pymarl2) | [![GitHub stars](https://img.shields.io/github/stars/hijkzzz/pymarl2)](https://github.com/hijkzzz/pymarl2/stargazers)    |       cooperative      |       1       |       Independent Learning(1) +  Centralized Critic(1) +  Value Decomposition(9)     |         full-sharing        |                   |   PyMARL
|   [MARL-Algorithms](https://github.com/starry-sky6688/MARL-Algorithms)| [![GitHub stars](https://img.shields.io/github/stars/starry-sky6688/MARL-Algorithms)](https://github.com/starry-sky6688/MARL-Algorithms/stargazers)  |       cooperative      |       1       |     CTDE(6) + Communication(1) + Graph(1) + Multi-task(1)   |         full-sharing        |  | *
|    [EPyMARL](https://github.com/uoe-agents/epymarl)| [![GitHub stars](https://img.shields.io/github/stars/uoe-agents/epymarl)](https://github.com/hijkzzz/uoe-agents/epymarl/stargazers)    |       cooperative      |       4       |    Independent Learning(3) + Value Decomposition(4) + Centralized Critic(2)    |        full-sharing + non-sharing       |                   |           PyMARL            | 
| [MAlib](https://github.com/sjtu-marl/malib) | [![GitHub stars](https://img.shields.io/github/stars/sjtu-marl/malib)](https://github.com/hijkzzz/sjtu-marl/malib/stargazers) | self-play | 2 +  [PettingZoo](https://www.pettingzoo.ml/) + [OpenSpiel](https://github.com/deepmind/open_spiel) | Population-based | full-sharing + group-sharing + non-sharing | :heavy_check_mark: | *
| [MAPPO Benchmark](https://github.com/marlbenchmark/on-policy)| [![GitHub stars](https://img.shields.io/github/stars/marlbenchmark/on-policy)](https://github.com/marlbenchmark/on-policy/stargazers) |     cooperative     |       4       |      MAPPO(1)     |         full-sharing + non-sharing        |         :heavy_check_mark:         |         pytorch-a2c-ppo-acktr-gail              |
|    [MARLlib](https://github.com/ICLR2023Paper4242/MARLlib)| |  cooperative collaborative competitive mixed  |       10 + [PettingZoo](https://www.pettingzoo.ml/)      |    Independent Learning(6) + Centralized Critic(7) + Value Decomposition(5)     |        full-sharing + group-sharing + non-sharing        |         :heavy_check_mark:         |           Ray/Rllib           |


## Installation


To use MARLlib, first install MARLlib, then install desired environments following [this guide](https://iclr2023marllib.readthedocs.io/en/latest/handbook/env.html), finally install patches for RLlib. After installation, training can be launched by following the usage section below.


### Install MARLlib

```bash
    conda create -n marllib python==3.8
    conda activate marllib
    # please install pytorch <= 1.9.1 compatible with your hardware.

    pip install ray==1.8.0
    pip install ray[tune]
    pip install ray[rllib]

    git clone https://github.com/ICLR2023Paper4242/MARLlib.git
    cd MARLlib
    pip install -e .
```


### Install environments

Please follow [this guide](https://iclr2023marllib.readthedocs.io/en/latest/handbook/env.html).

### Install patches for RLlib

We fix bugs of RLlib by providing patches. After installing Ray, run the following command:

```
cd /Path/To/MARLlib/patch
python add_patch.py -y
```

For pommerman users, run

```
cd /Path/To/MARLlib/patch
python add_patch.py -y -p
```



## Usage

### Step 1. Prepare the configuration files

<div align="center">
<img src=image/configurations.png width=100% />
</div>

There are four configuration files you need to ensure correctness for your training demand. 

- scenario: specify your environment/task settings
- algorithm: finetune your algorithm hyperparameters
- model: customize the model architecture
- ray/rllib: changing the basic training settings

### Step 2. Making sure all the dependency are installed for your environment.

You can refer to [here](https://iclr2023marllib.readthedocs.io/en/latest/handbook/env.html) to install the environment.
After everything settled, make sure to change back you Gym version to 1.21.0.
All environment MARLlib supported should work fine with this version.

```
pip install gym==1.21.0
```

### Step 3. Start training

```
cd /Path/To/MARLlib
python marl/main.py --algo_config=$algo [--finetuned] --env_config=$env with env_args.map_name=$map
```

Available algorithms (case sensitive):

- iql
- pg
- a2c
- ddpg
- trpo
- ppo
- maa2c
- coma
- maddpg
- matrpo
- mappo
- hatrpo
- happo
- vdn
- qmix
- facmac
- vda2c
- vdppo

Available env-map pairs (case sensitive):

- smac: [smac maps](https://github.com/oxwhirl/smac/blob/master/smac/env/starcraft2/maps/smac_maps.py)
- mpe: [mpe map](https://github.com/ICLR2023Paper4242/MARLlib/blob/main/envs/base_env/mpe.py)
- mamujoco: [mamujoco map](https://github.com/ICLR2023Paper4242/MARLlib/blob/main/envs/base_env/mamujoco.py)
- football: [football map](https://github.com/ICLR2023Paper4242/MARLlib/blob/main/envs/base_env/mamujoco.py)
- magent: [magent map](https://github.com/ICLR2023Paper4242/MARLlib/blob/main/envs/base_env/magent.py)
- lbf: use [lbf config](https://github.com/ICLR2023Paper4242/MARLlib/blob/main/envs/base_env/config/lbf.yaml) to generate the map. Details can be found https://github.com/semitable/lb-foraging#usage
- rware: use [rware config](https://github.com/ICLR2023Paper4242/MARLlib/blob/main/envs/base_env/config/rware.yaml) to generate the map. Details can be found https://github.com/semitable/robotic-warehouse#naming-scheme
- pommerman: OneVsOne-v0, PommeFFACompetition-v0, PommeTeamCompetition-v0
- metadrive: Bottleneck, ParkingLot, Intersection, Roundabout, Tollgate
- hanabi: Hanabi-Very-Small, Hanabi-Full, Hanabi-Full-Minimal, Hanabi-Small

--finetuned is optional, force using the finetuned hyperparameter if available in [this directory](https://github.com/ICLR2023Paper4242/MARLlib/tree/main/marl/algos/hyperparams/finetuned)


Example on SMAC:

```
python marl/main.py --algo_config=MAPPO [--finetuned] --env_config=smac with env_args.map_name=3m
```

--finetuned is optional, force using the finetuned hyperparameter if available.



## Navigation

We provide an introduction to the code directory to help you get familiar with the codebase.

**Top level directory structure:**

<div align="center">
<img src=image/code-MARLlib.png width=120% />
</div>

**MARL directory structure:**

<div align="center">
<img src=image/code-MARL.png width=70% />
</div>

**ENVS directory structure:**

<div align="center">
<img src=image/code-ENVS.png width=70% />
</div>


## Experiment Results

All results are listed [here](https://github.com/ICLR2023Paper4242/MARLlib/tree/main/results).

## Contribute

MARLlib is friendly to incorporating a new environment. Besides the ten we already implemented, we support almost all kinds of MARL environments.
Before contributing new environment, you must know:

Things you ought to cover:

- provide a new environment interface python file, follow the style of [MARLlib/envs/base_env](https://github.com/ICLR2023Paper4242/MARLlib/tree/main/envs/base_env)
- provide a corresponding config yaml file, follow the style of [MARLlib/envs/base_env/config](https://github.com/ICLR2023Paper4242/MARLlib/tree/main/envs/base_env/config)
- provide a corresponding instruction readme file, follow the style of [MARLlib/envs/base_env/install](https://github.com/ICLR2023Paper4242/MARLlib/tree/main/envs/base_env/install)

Things not essential:

- change the MARLlib data processing pipeline
- provide a unique runner or controller specific to the environment 
- concern about the data logging 

The ten environments we already contained have covered great diversity in action space,  observation space, agent-env interaction style, task mode, additional information like action mask, etc. 
The best practice to incorporate your environment is to find an existing similar one and provide the same interface.


    