# Space-Efficient Folding Algorithm Pipeline

## Overview

This project implements a **space-efficient unfolding and nesting algorithm** using the **Packaide** nesting library. The goal is to generate multiple unfoldings of a given 3D model, optimize how they fit within a 2D space, and select the most efficient configuration.

## Features

- Uses **Packaide** to optimize space utilization by nesting unfoldings efficiently.
- Evaluates space efficiency using the **bounding box method**.
- Compares multiple predefined unfoldings and selects the most efficient one.
- Displays the original and nested versions of each unfolding candidate.

## Usage

### Running the Notebook

- Open the Jupyter Notebook: `SpaceEfficientAlg_pipeline.ipynb`.
- Run the cells **sequentially** to:
  - Load predefined cube unfoldings.
  - Use **Packaide** to nest the unfoldings efficiently.
  - Evaluate and compare space efficiency.
  - Select the best unfolding based on utilization ratio.
  - Output the best nesting configuration found.

### Testing Packaide Setup

To verify that **Packaide** is installed correctly, run:

```python
import packaide
print("Packaide imported successfully!")
```

## Algorithm Details

### 1. Candidate Unfoldings

- The project defines **multiple predefined unfoldings** for a cube.
- These unfoldings are **hardcoded SVG strings**.

### 2. Nesting the Unfoldings with Packaide

- The algorithm passes each unfolding to **Packaide**, which attempts to place it on a **2D sheet**.
- Packaide tries to **minimize the unused space** between the nested parts.

### 3. Evaluating Packing Efficiency

- **Bounding Box Method**: Measures the enclosing rectangular area.
- **Utilization Ratio**: Computes how much of the bounding box area is used effectively.
- **Comparison**: The algorithm compares utilization ratios across candidates.

## Parameters

The algorithm allows tweaking various parameters for better results:

| Parameter            | Description                                                                         |
| -------------------- | ----------------------------------------------------------------------------------- |
| **Tolerance**        | Controls the precision of shape discretization (higher = more accurate but slower). |
| **Offset**           | Adds a margin around parts to prevent overlaps.                                     |
| **Partial Solution** | If True, allows placement of as many parts as possible, even if some don’t fit.     |
| **Rotations**        | Determines how many orientations Packaide should attempt.                           |
| **Persist**          | Enables caching to speed up repeated nesting computations.                          |

## Output

- The script identifies and visualizes the **best unfolding candidate** based on **highest utilization ratio**.
- The best nested layout is saved as **optimal\_unfolding.svg**.

## Example Results

Each predefined unfolding is evaluated and displayed with:

- **Original unfolding layout**
- **Packed version (after nesting)**
- **Utilization ratio per candidate**

```sh
Candidate 1:
  Original Utilization: 0.65
  Packed Utilization: 0.72

Candidate 2:
  Original Utilization: 0.72
  Packed Utilization: 0.79

Best candidate: Final configuration with utilization ratio: 0.85
```

## Future Improvements

- Implement an **iterative feedback loop** to refine unfoldings dynamically.
- Extend to **arbitrary 3D models** beyond cubes.
- Implement **machine learning-based optimizations** for better cutting strategies.

## Contributors

- Abiel Yacob
- Abdelrahman Khattab
