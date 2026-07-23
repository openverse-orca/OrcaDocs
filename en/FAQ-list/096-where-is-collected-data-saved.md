# Where is collected data saved?

## Question
After data collection through OrcaLab's VR teleoperation mode, where are the various generated data (such as robot joint data, sensor data, VR controller data, etc.) saved on my computer? How can I find this data?

## Answer

Data collected in OrcaLab's VR teleoperation mode is typically saved by the **data collection script** to a specified directory on your local computer. This data is an important foundation for subsequent AI training or behavior analysis.

## 📋 Data Collection Results Storage Location

### 1. **Specified by the Data Collection Script**
-   The data collection script (such as `data_collection_tele.py`) typically has built-in logic to save collected data to a preset directory.
-   This directory is usually a subdirectory under the script's **current working directory**, or specified through **command-line arguments** or a **configuration file** (such as `example.yaml`).

### 2. **Check Terminal Output**
-   When you run the data collection script, the terminal displays log information in real-time. After data is successfully saved, the script typically **explicitly indicates the path where data was saved**.



#### Example Terminal Output (Pseudocode)
```
...
[INFO] Data collection started for episode 1.
[INFO] Saving collected data to: /home/user/OrcaManipulation/data/2024-01-22_15-30-00_shop_pick_and_place/episode_001.hdf5
[INFO] Data collection finished. Press trigger for next episode or 'q' to quit.
...
```

### 3. **Check the Script's Configuration File**
-   Data collection tasks typically have a corresponding configuration file (such as `example.yaml`), which may contain parameters for data save path, file name format, etc.
-   Open the configuration file and look for relevant fields such as `output_dir`, `data_path`, `save_location`.

#### Example Configuration File Fragment (Pseudocode from OrcaManipulation `example.yaml`)
```yaml
# ...
output:
  base_dir: "./data"  # Base directory for data saving
  format: "hdf5"      # Data file format
  naming_convention: "{timestamp}_{level_name}/{episode}.{format}"
# ...
```

### 4. **Check the Script Source Code**
-   If none of the above methods can determine the save path, you can directly consult the source code of the data collection script (such as `data_collection_tele.py`).
-   Search for function calls like `open()`, `write()`, `save()`, `os.path.join` in the code to find the actual file writing logic and paths.

## 📁 Data Storage Formats & Content

Data collection scripts typically store data in **structured file formats** for subsequent processing. Common data formats include:

### 1. **HDF5 (.hdf5)**
-   **Characteristics**: Suitable for storing large, complex, heterogeneous scientific data. Supports hierarchical storage and efficient read/write.
-   **Content**: May include robot joint positions/velocities/torques, end-effector poses, VR controller poses, sensor readings (camera images, depth maps, LiDAR point clouds), timestamps, task states, rewards, etc.

### 2. **NumPy (.npy / .npz)**
-   **Characteristics**: Used for efficient storage and loading of NumPy arrays, suitable for large amounts of numerical data.
-   **Content**: Robot trajectories, sensor sequence data, etc.

### 3. **JSON (.json)**
-   **Characteristics**: Lightweight data interchange format, easy for humans to read and machines to parse.
-   **Content**: Task configuration, metadata, small amounts of structured data, or logs.

### 4. **Image/Video Files (.png, .jpg, .mp4, .avi)**
-   **Characteristics**: Images or recorded video collected by camera sensors, typically stored in subfolders under the data directory.

## 💡 Best Practices

### 1. **Customize Output Path**
-   When running the data collection script, specify a clear, easily manageable output directory through command-line arguments or by modifying the configuration file, for example:
    ```bash
    python data_collection_tele.py --output-dir /home/user/my_robot_data/experiment_A
    ```

### 2. **Structured Naming**
-   Use meaningful naming conventions to organize your data files, e.g., `{task_name}_{date}_{time}/{episode_id}.hdf5`.
-   This helps quickly find and manage vast amounts of data.

### 3. **Back Up Important Data**
-   Regularly back up important collected data to prevent hard drive failure or accidental deletion.

### 4. **Metadata**
-   In addition to raw data, ensure metadata related to the data is also saved, such as: robot model, sensor types, simulation parameters, random seed, task description, operator information, etc. This is crucial for data analysis and reproducibility.

## ⚠️ Important Notes

### 1. **Disk Space**
-   Data collection, especially when including images and point cloud data, can generate very large data volumes. Ensure your hard drive has sufficient space.

### 2. **File Permissions**
-   Ensure the user running the data collection script has permission to create and write files in the specified output directory.

## 📝 Summary

Data collected through OrcaLab's VR teleoperation is typically saved by Python scripts to a specified directory, which can be determined through terminal output, script configuration files, or by directly consulting the script source code. Data is typically stored in formats such as HDF5, NumPy, and JSON. It is recommended to customize the output path and use structured naming, and regularly back up important data.

## Related Links
- [VR Teleoperation & Data Collection Guide](user-guide/data-collection-and-synthesis/vr-teleoperation-and-data-collection-guide.md)
- [How to run data collection scripts?](FAQ-list/095-how-to-run-data-collection-scripts.md)
- [Data Collection Task Configuration File Description](user-guide/data-collection-and-synthesis/vr-teleoperation-and-data-collection-guide.md)
- [How to save and export simulation results?](FAQ-list/085-how-to-save-and-export-simulation-results.md)