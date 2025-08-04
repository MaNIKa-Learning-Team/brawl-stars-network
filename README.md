# Brawl Stars Character Balancing

This is a Network Science project aimed at aiding in the character balancing of [Brawl Stars](https://en.wikipedia.org/wiki/Brawl_Stars) by identifying potentially dominant or underperforming characters using player-game interaction networks.

## Context

[Brawl Stars](https://en.wikipedia.org/wiki/Brawl_Stars) is a fast-paced third-person shooter developed by [Supercell](https://en.wikipedia.org/wiki/Supercell_(company)) for Android and iOS. It features over 90 unique characters ("brawlers") and a variety of competitive game modes. As of 2021, it became Supercell’s fourth title to surpass US$1 billion in lifetime revenue.

### Problem Statement

As the roster grows, new and casual players face a steep learning curve. The complexity of learning 90+ characters—each with distinct mechanics, roles, and optimal game modes—can discourage continued play. This negatively impacts **player acquisition**, **early-stage retention**, and ultimately, **revenue**.

#### Supporting Evidence

This hypothesis is supported by a notable **decline in monthly downloads** and **in-app purchase revenue** since early 2024, as reported by [Statista](https://www.statista.com/statistics/1358816/global-brawl-stars-iap-revenue/). Additionally, player reviews and forum posts have raised concerns over balance and meta complexity, particularly for new players.

---

### Objective

This project uses network science techniques to:
- Map relationships between brawlers, players, and game outcomes
- Detect meta-centrality and balance issues
- Recommend data-driven balancing actions (e.g., buffs, nerfs, bans, or restrictions)

The goal is to demonstrate how network-based analytics can guide game balancing decisions that **improve player experience** and **enhance long-term monetization**.

## Environment Setup
This project uses [`uv`](https://github.com/astral-sh/uv), a fast and modern Python package manager and virtual environment tool. The setup below ensures that all team members can create an isolated environment and install dependencies consistently.

---

### 1. Install `uv` (one-time setup)
```
pip install --user uv
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

This installs `uv` to your user directory and updates your shell configuration so you can run `uv` from any terminal.

### 2. Verify the installation
```
uv --version
```

### 3. Create the virtual environment
From the **root of this repository**:

```
uv venv .venv
source .venv/bin/activate
```

This creates a virtual environment named `.venv/` inside the project folder and activates it. `.venv/` is excluded from version control using `.gitignore` so that each developer can maintain their own clean environment.

### 4. Install project dependencies
```
uv sync
```

This installs exact versions of all packages as specified in `uv.lock`. Use this for reproducibility across machines and environments.

### 5. Register the kernel
```
python -m ipykernel install --user --name=brawl-stars --display-name "Brawl Stars"
```

Registering the kernel is what makes your virtual environment usable inside Jupyter Notebooks, especially in JupyterHub, which may not automatically detect environments.

## Activating the Environment
Activate the `uv` virtual environment by running

```
source .venv/bin/activate
``` 

in the project root.

## Reset or Recreate the Environment
If you ever need to start fresh:

```
rm -rf .venv
uv venv .venv
source .venv/bin/activate
uv sync
```

## Adding a New Package
To add a new package to the project:

```
uv pip install <package-name>
```

To add a development-only package:

```
uv pip install <package-name> --group dev
```

This keeps your main dependencies clean by putting dev tools (like formatters, linters, or test libraries) in a separate group. That way, production installs stay lightweight, and only developers install the extra tools they need.

The two commands above update `pyproject.toml` and `uv.lock` automatically.

After adding, other team members just need to run:

```
uv sync
```

to install the new package.

## Notes
- Do not use `pip install` directly. Use `uv add` to track and lock packages properly.