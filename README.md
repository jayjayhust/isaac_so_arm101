# SO-100 Robot Cube Lifting Environment

## Overview

This project is an external project for Isaac Lab that implements a cube lifting task using the SO-100 robot arm. For more information about external projects in Isaac Lab, see the [documentation](https://isaac-sim.github.io/IsaacLab/main/source/overview/developer-guide/template.html).

## URDF Modifications

The URDF file for the SO-100 robot arm has been modified to fix compatibility issues with Isaac Sim. Special thanks to the following Discord contributors for their help in identifying and fixing these issues:

- Robert K - Identified and fixed issues with the Moving Jaw naming in URDF
- robopie - Identified the correct URDF version to use and helped with troubleshooting
- Fichtl - Provided insights on hardware setup and testing

The main modifications include:
- Renamed "Moving Jaw" to "Moving_Jaw" in link names and mesh references
- Fixed mesh file references to ensure proper import into Isaac Sim
- Ensured consistent naming conventions across the URDF structure

## Installation

1. Install Isaac Lab by following the [installation guide](https://isaac-sim.github.io/IsaacLab/main/source/setup/installation/index.html).
   We recommend using conda installation as it simplifies calling Python scripts from the terminal.

2. Install this project in editable mode:
   ```bash
   python -m pip install -e source/SO_100
   ```

## Usage
(Ensure your Isaac Lab conda environment is activated before running these commands)

### List Available Tasks
Verify that the SO-100 environment is registered:
```bash
python scripts/list_envs.py
```
You should see `Template-So-100-CubeLift-v0` in the output.

### Train the Agent

To watch training with a small number of environments:
```bash
# Training with visual feedback (32 environments)
python scripts/skrl/train.py --task Template-So-100-CubeLift-v0 --num_envs 32
```

To accelerate training (more environments, no graphical interface):
```bash
# Headless training with more environments
python scripts/skrl/train.py --task Template-So-100-CubeLift-v0 --num_envs 4096 --headless
```

Training logs and checkpoints will be saved under the `logs/skrl/SO100_lift/` directory.

### Play/Evaluate the Agent

Run a trained policy:
```bash
python scripts/skrl/play.py --task Template-So-100-CubeLift-v0 --checkpoint logs/skrl/SO100_lift/<YOUR_RUN_DIR>/checkpoints/agent_<STEP>.pt
```

> **Note**: Make sure to add `logs/skrl/SO100_lift/` to your `.gitignore` file to avoid committing large training files.

## Building Your Own Project or Task

Traditionally, building new projects that utilize Isaac Lab's features required creating your own extensions within the Isaac Lab repository. However, this approach can obscure project visibility and complicate updates from one version of Isaac Lab to another. To circumvent these challenges, we now provide a command-line tool (template generator) for creating Isaac Lab-based projects and tasks.

The template generator enables you to create:

### External project (recommended)
An isolated project that is not part of the Isaac Lab repository. This approach works outside of the core Isaac Lab repository, ensuring that your development efforts remain self-contained. Also, it allows your code to be run as an extension in Omniverse.

> **Hint**: For the external project, the template generator will initialize a new Git repository in the specified directory. You can push the generated content to your own remote repository (e.g. GitHub) and share it with others.

### Internal task
A task that is part of the Isaac Lab repository. This approach should only be used to create new tasks within the Isaac Lab repository in order to contribute to it.

## Installation Guide

### Prerequisites
1. Install Isaac Lab by following the [installation guide](https://isaac-sim.github.io/IsaacLab/main/source/setup/installation/index.html).
   We recommend using conda installation as it simplifies calling Python scripts from the terminal.

### Running the Template Generator

Run the following command to generate a new external project or internal task:

**Linux**:
```bash
./isaaclab.sh --new  # or "./isaaclab.sh -n"
```

**Windows**:
```bash
isaaclab.bat --new  # or "isaaclab.bat -n"
```

The generator will guide you in setting up the project/task by asking about:
- Type of project/task (external or internal)
- Project/task path or names
- Isaac Lab workflows
- Reinforcement learning libraries and algorithms

### External Project Usage

Once the external project is generated:

1. Install the project in editable mode:
   ```bash
   # Linux/Windows
   python -m pip install -e source/<given-project-name>
   ```

2. List available tasks:
   ```bash
   # Linux/Windows
   python scripts/list_envs.py
   ```
   > **Note**: If task names change, update the search pattern "Template-" in scripts/list_envs.py

3. Run a task:
   ```