# How to save and export simulation results?

## Question
After running a simulation in OrcaLab, I have generated a large amount of simulation data and visualization results. How should I save this data and export it for subsequent analysis, reporting, or integration with other tools?

## Answer

As a simulation system, one of OrcaLab's core goals is to generate and process data. Saving and exporting simulation results is typically done through **Python scripts within the simulation program**, covering various forms such as data, images, and video.

## 📋 Saving and Exporting Simulation Results

### 1. **Data Saving (via Python Scripts)**

#### Purpose
-   Save numerical data generated during simulation, such as robot joint states, sensor readings, object positions and poses, environment parameters, reward values, AI model intermediate states, etc.

#### Common Formats
-   **CSV/TXT**: The simplest text format, suitable for structured data.
    ```python
    import csv
    data = [['timestamp', 'joint_pos'], [0.1, 0.5], [0.2, 0.6]]
    with open('output_data.csv', 'w', newline='') as f:
        writer = csv.writer(f)
        writer.writerows(data)
    ```
-   **NumPy `.npy` / `.npz`**: Suitable for saving NumPy arrays; efficient and compact.
    ```python
    import numpy as np
    joint_data = np.array([[0.1, 0.5], [0.2, 0.6]])
    np.save('joint_data.npy', joint_data)
    ```
-   **JSON/YAML**: Suitable for saving structured configuration or log data.
    ```python
    import json
    config_log = {'episode': 1, 'reward': 100}
    with open('config_log.json', 'w') as f:
        json.dump(config_log, f, indent=4)
    ```
-   **HDF5/Pickle**: Suitable for saving large, complex datasets or Python objects.

#### Operation
-   In your simulation Python script, use Python's standard library or third-party libraries (such as `numpy`, `pandas`, `json`, etc.) to write data to files.
-   Define clear data structures and file naming conventions for easier subsequent management.

### 2. **Image Saving (via Python Scripts or Client Screenshots)**

#### Purpose
-   Save images generated during simulation for visual analysis, reporting, or AI training (such as visual perception models).

#### Method 1: Save Rendered Images via Python Scripts
-   OrcaLab's Python API typically provides interfaces that allow you to obtain rendered images (RGB, depth, semantic segmentation, etc.) from cameras in the simulation environment and save them in common image formats (PNG, JPG).
    ```python
    # Example pseudocode: actual API calls may differ
    camera_image = orcalab_env.get_camera_image('robot_camera')
    cv2.imwrite('frame_001.png', camera_image)
    ```

#### Method 2: Client Screenshots
-   You can use the operating system's built-in screenshot tool (such as Ubuntu's screenshot tool) or third-party screenshot software to capture the display in the OrcaLab client's 3D viewport.

### 3. **Video Saving (via Python Scripts or Client Recording)**

#### Purpose
-   Record dynamic video of the simulation process for demonstration, analyzing robot behavior, or creating teaching materials.

#### Method 1: Record Video via Python Scripts
-   OrcaLab's Python API may provide video recording interfaces, allowing you to specify recording framerate, encoder, and output file.
    ```python
    # Example pseudocode: actual API calls may differ
    orcalab_env.start_video_recording('simulation_video.mp4', fps=30)
    # Run simulation...
    orcalab_env.stop_video_recording()
    ```
-   Alternatively, you can obtain frame-by-frame images from cameras and then use tools like `OpenCV` or `ffmpeg` to combine these images into a video.

#### Method 2: Client Recording (If Supported)
-   The OrcaLab client may have built-in video recording functionality (typically in the menu bar or toolbar). If available, this is the most convenient recording method.
-   **Note**: OrcaLab may depend on libraries such as `libx265-dev` to support video encoding.

## 💡 Export Best Practices

### 1. **Structured Storage**
-   Create a separate directory for each simulation experiment and store all related data, images, videos, configuration files, and log files together.
-   Use clear file naming conventions that include information such as timestamps and experiment parameters.

### 2. **Data Standardization**
-   Use standardized data formats (such as ROS bag, OpenDRIVE, USD) whenever possible to save scene descriptions and robot data, facilitating integration with other tools or platforms.

### 3. **Metadata Recording**
-   Save important metadata along with simulation results, such as simulation version, parameter configuration, random seed, AI model version, etc. This is crucial for result reproducibility and analysis.

### 4. **Version Control**
-   Use Git for version control of important simulation code and configuration files.
-   For smaller-scale simulation results, consider managing them with Git LFS (Large File Storage).

### 5. **Visualization Tools**
-   Use Python libraries such as `matplotlib`, `seaborn`, `plotly` for visual analysis of exported data.

## ⚠️ Important Notes

### 1. **Data Volume**
-   High-frequency data collection and high-resolution image/video recording generate large amounts of data. Ensure your hard drive space is sufficient.

### 2. **Performance Impact**
-   Real-time data writing to disk and video encoding may have some impact on simulation performance, especially on resource-limited systems.

### 3. **File Permissions**
-   Ensure your Python scripts have sufficient permissions when attempting to write files.

### 4. **Data Security**
-   Regularly back up important simulation results to prevent data loss.

## 📝 Summary

OrcaLab simulation results are primarily saved and exported through **Python scripts within the simulation program**, supporting various data formats, image, and video generation. The client may also provide screenshot and recording functionality. By following best practices such as structured storage, data standardization, and version control, simulation results can be efficiently managed and utilized.

## Related Links
- [VR Teleoperation & Data Collection Guide](user-guide/data-collection-and-synthesis/vr-teleoperation-and-data-collection-guide.md)
- [How to view simulation logs?](FAQ-list/082-how-to-view-simulation-logs.md)
- [How accurate is OrcaLab's physics simulation?](FAQ-list/010-how-accurate-is-orcalab-physics-simulation.md)