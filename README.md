# Project Manas: An ARC Prize 2025 Solver

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Kaggle Competition](https://img.shields.io/badge/Kaggle-ARC%20Prize%202025-blue.svg)](https://www.kaggle.com/competitions/arc-prize-2025)

This repository contains the source code for **Project Manas**, an AI solver developed for the [ARC Prize 2025](https://www.kaggle.com/competitions/arc-prize-2025), a Kaggle competition focused on Artificial General Intelligence (AGI).

---

## Overview

The Abstraction and Reasoning Corpus (ARC) is a benchmark designed to test an AI's ability to acquire new skills and solve novel problems from a handful of examples. This project aims to tackle the ARC challenge by moving beyond conventional machine learning models and instead focusing on **program synthesis**—the automatic generation of computer programs from high-level specifications.

The core of this solver is an engine that attempts to deduce the underlying logic of a puzzle and express that logic as a simple program.

---

## Core Philosophy

This solver is built on the belief that true abstract reasoning, as required by ARC, is not a task of statistical pattern matching but of algorithmic inference. Instead of training a large neural network on thousands of examples, this solver analyzes the structure of each puzzle and searches for a sequence of logical steps that transforms the input into the desired output.

The approach is composed of three main components:

1.  **Perception Module (The "Eyes")**: This component analyzes a raw puzzle grid and identifies distinct objects, their properties (color, size, shape), and their positions. It turns unstructured pixel data into a structured, symbolic representation.

2.  **Domain-Specific Language (DSL) (The "Hands")**: This is a powerful library of fundamental operations that can be performed on the grid or the objects within it. The DSL includes functions for moving, recoloring, rotating, flipping, and deleting objects and the grid itself.

3.  **Program Synthesis Engine (The "Brain")**: This is the reasoning core of the solver. It uses a **Breadth-First Search (BFS)** algorithm to explore combinations of DSL functions, searching for a sequence (a "program") that successfully solves all the training examples for a given task.

---

## How It Works

For each puzzle, the solver follows a distinct process:

1.  **Analyze**: It first looks at the training pairs to understand the task.
2.  **Generate Candidates**: It creates a list of plausible transformations using its DSL.
3.  **Search**: The BFS engine searches for a sequence of these transformations (e.g., "rotate the grid 90 degrees, then move the largest object down by 2 spaces") that consistently solves all training pairs.
4.  **Validate**: The identified program must work for every single training example.
5.  **Predict**: If a valid program is found, the solver applies that exact sequence of steps to the test grids to generate the final predictions. If no solution is found within the search limits, it defaults to submitting the original input grid.

---

## How to Run

This project is designed to be run as a self-contained Kaggle Notebook.

1.  Navigate to the [ARC Prize 2025 competition](https://www.kaggle.com/competitions/arc-prize-2025) on Kaggle.
2.  Upload the `Project-Abstraction.ipynb` notebook.
3.  Commit and run the notebook, then submit the generated `submission.json` file.

---

## License

This project is licensed under the **Creative Commons Attribution 4.0 International License**. See the [LICENSE](LICENSE) file for details. This is in accordance with the open-sourcing requirements for prize-eligible submissions in the ARC Prize 2025 competition.

---

## Citation

If you reference this project, please cite the original competition:

```
Francois Chollet, Mike Knoop, Greg Kamradt, Walter Reade, and Addison Howard. ARC Prize 2025. [https://kaggle.com/competitions/arc-prize-2025](https://kaggle.com/competitions/arc-prize-2025), 2025. Kaggle.

