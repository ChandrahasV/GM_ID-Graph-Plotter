# Gm/Id Methodology Plotting Tool

## Overview
This project is based on the `lookup.m` and `lookupVGS.m` functions originally developed by Paul Jespers and Boris Murmann in their book *Systematic Design of Analog CMOS Circuits*. These MATLAB functions were used to analyze and extract parameters from transistor simulation data.

In this project, these functions are translated into Python to make them easier to use and more widely accessible. A simple GUI has also been created using PyQt5 and the `lookup.py` function to help plot transistor characteristic graphs quickly, removing the need for repetitive MATLAB scripting for generating the numerous graphs required when applying this methodology.

## Lookup and LookupVGS functions in python 
### 1. Lookup Function
The `lookup` function mimics the MATLAB version. Here’s a breakdown:

#### Syntax:
```python
lookup(data, 'output', 'input1', value1, 'input2', value2, ...)
```
- **`data`**: The `.mat` data, converted to a NumPy array using `scipy.io.loadmat`.
- **`output`**: The desired output parameter (string).
- **`input`**: Input parameter(s) (string).
- **`value`**: Value(s) for the corresponding input parameter. For stepwise arrays, use `np.arange(start, stop, step)`.

#### Examples:
```python
lookup(nch_data, 'ID', 'L', np.arange(0.4, 1.8, 0.2), 'VGS', 0.5)
```
Both `lookup` and `lookupvgs` functions come with extensive examples demonstrating their usage. Refer to those examples provided in the codebase in case of any doubts regarding their usage.

## Usage Instructions for the plotter
This tool simplifies graph generation, avoiding repetitive coding for plotting graphs in MATLAB.

### Steps:
1. **Upload your `.mat` file**.
2. **Select axes**: Choose `y1`, `y2`, or both for the y-axes and define the x-axis.
3. **Provide inputs**: Specify up to 4 inputs. 
   - For multiple values, separate them with commas (e.g., `0.4, 0.5, 0.6`).
   - For stepwise values, use a colon-separated format (e.g., `0.4:0.1:0.7`).
4. **Update the plot**: Click the "Update Plot" button.
5. **X-Slider**:
   - If inputs contain a varying parameter, use the x-slider to view how y-values change for a fixed x-value.
   - For instance, observe how `gm/gds` varies with `L` for a specific `gm/id` value.
   - No graph is generated if no varying parameter is present.
   - Use the magnifying glass and zoom out buttons in the toolbar to explore the graph.

## Dependencies
- Python (>=3.6)
- NumPy
- SciPy
- Matplotlib
- PyQt5

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/your-repo/gm-id-tool.git
   ```
2. Install the dependencies:
   ```bash
   pip install -r requirements.txt
   ```
---
Feel free to contribute or raise issues to improve this project!
