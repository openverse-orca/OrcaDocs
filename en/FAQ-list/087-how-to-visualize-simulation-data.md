# How to visualize simulation data?

## Question
After running an OrcaLab simulation, I have obtained a large amount of simulation data. How should I perform visual analysis on this data to better understand simulation results, debug algorithms, or create report presentations?

## Answer

Visualizing simulation data is an indispensable part of understanding, analyzing, and debugging OrcaLab simulation results. Since OrcaLab's simulation programs are typically controlled and generate data through Python scripts, leveraging **Python's powerful data analysis and visualization libraries** is the primary and recommended approach.

## 📋 Simulation Data Visualization Strategies

### 1. **Real-Time Visualization (via OrcaLab Client)**

#### Purpose
-   The OrcaLab client's 3D viewport is itself a real-time visualization tool, displaying object motion, physical interactions, and robot behavior during the simulation.
-   The "Terminal Panel" also displays the program's log output in real-time, including some text-based statistical data.

#### Advantages
-   Intuitive, no additional development required.
-   Strong real-time capability, convenient for observing the simulation process.

#### Disadvantages
-   Limited to the visual representation of the 3D scene.
-   Cannot perform deep analysis and plotting of underlying numerical data.



### 2. **Offline Visualization (via Python Libraries)**

This is the primary approach for in-depth analysis and professional presentation of simulation data. You need to save simulation data to files, then process it using Python scripts.

#### Common Python Visualization Libraries

-   **Matplotlib**: The most basic and widely used 2D plotting library in Python, capable of creating line plots, scatter plots, bar charts, histograms, etc.
    ```python
    import matplotlib.pyplot as plt
    import numpy as np

    # Example with some joint position data
    time = np.linspace(0, 10, 100)
    joint_pos = np.sin(time)

    plt.figure(figsize=(10, 6))
    plt.plot(time, joint_pos, label='Joint Position')
    plt.xlabel('Time (s)')
    plt.ylabel('Position (rad)')
    plt.title('Robot Joint Position over Time')
    plt.legend()
    plt.grid(True)
    plt.show()
    plt.savefig('joint_position.png')
    ```

-   **Seaborn**: Built on Matplotlib, provides a higher-level statistical graphics interface, producing more visually appealing graphs with more concise code.
    ```python
    import seaborn as sns
    import pandas as pd

    # Example with a DataFrame containing reward data
    data = {'Episode': range(100), 'Reward': np.random.rand(100).cumsum()}
    df = pd.DataFrame(data)

    sns.lineplot(x='Episode', y='Reward', data=df)
    plt.title('Reinforcement Learning Reward Curve')
    plt.show()
    ```

-   **Plotly/Bokeh**: Used to create interactive graphics that can be viewed in a web browser, supporting operations such as zoom and pan.
    ```python
    import plotly.graph_objects as go

    fig = go.Figure(data=go.Scatter(x=time, y=joint_pos, mode='lines'))
    fig.update_layout(title='Interactive Joint Position', xaxis_title='Time', yaxis_title='Position')
    fig.show()
    ```

-   **OpenCV**: Primarily used for image and video processing, but can also be used to load, display, and save simulation-generated images or video frames.
    ```python
    import cv2

    # Load a simulation-generated image
    img = cv2.imread('frame_001.png')
    cv2.imshow('Simulation Frame', img)
    cv2.waitKey(0)
    cv2.destroyAllWindows()
    ```

### 3. **3D Data Visualization (Advanced)**

#### Purpose
-   For more complex 3D data (such as point clouds, robot motion trajectories, physics fields), specialized 3D visualization tools may be needed.

#### Common Libraries/Tools
-   **Mayavi / VisPy**: Based on VTK, used for scientific 3D visualization in Python.
-   **Blender Python API**: If OrcaLab supports exporting to Blender, advanced 3D visualization and animation can be done in Blender.
-   **Custom 3D Rendering**: If OrcaLab provides lower-level 3D data access interfaces, users can develop their own 3D visualization through OpenGL/Vulkan or dedicated rendering libraries.

## 💡 Best Practices

### 1. **Choose Appropriate Data Formats**
- **Numerical Data**: Prioritize using `.npy`, `.npz`, or HDF5 (`.h5`) for saving large amounts of numerical data; highly efficient.
- **Structured Data**: Use CSV, JSON, YAML for saving configurations, logs, and small amounts of structured data.

### 2. **Organize Data**
- Store different types of data (such as sensor data, joint data, reward curves) separately.
- Use clear directory structures and file names to organize the data from each simulation experiment.

### 3. **Code Reuse**
- Write reusable visualization functions or scripts for application across different simulation experiments to improve efficiency.

### 4. **Interactive Analysis**
- Use interactive environments such as Jupyter Notebook or IPython for data exploration and visualization, facilitating rapid iteration.

## ⚠️ Important Notes

### 1. **Data Volume**
- Large amounts of simulation data (especially high-framerate images and videos) can consume significant disk space. Ensure sufficient storage is available.

### 2. **Real-Time Requirements**
- Offline visualization is primarily used for post-hoc analysis. If real-time data visualization is needed, the OrcaLab client interface is the primary tool, or custom real-time monitoring tools need to be developed.

### 3. **Data Security**
- Regularly back up important simulation data to prevent accidental loss.

## 📝 Summary

OrcaLab simulation data visualization is primarily achieved through **Python's powerful data analysis and plotting libraries** (such as Matplotlib, Seaborn, Plotly) for offline analysis and presentation. The client's 3D viewport provides real-time intuitive visualization. By choosing appropriate data formats, organizing data, and writing efficient Python scripts, valuable insights can be effectively extracted from simulation data.

## Related Links
- [How to save and export simulation results?](FAQ-list/083-how-to-save-and-export-simulation-results.md)
- [How to view simulation logs?](FAQ-list/080-how-to-view-simulation-logs.md)
- [How to set the simulation time step?](FAQ-list/086-how-to-set-simulation-time-step.md)