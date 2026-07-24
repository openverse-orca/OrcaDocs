# How to improve simulation speed?

## Question
When running simulations in OrcaLab, I feel the speed is slow or the framerate (FPS) is low. How can I optimize settings and the environment to improve OrcaLab's simulation speed and smoothness?

## Answer

Improving OrcaLab's simulation speed involves multiple aspects including **hardware optimization, software configuration adjustment, and scene complexity management**. As a high-fidelity physics AI simulation system, OrcaLab has high performance requirements, and proper optimization can significantly enhance the experience.

## 📋 Strategies for Improving Simulation Speed

### 1. **Optimize Hardware Configuration (Fundamental Solution)**

#### Measures
-   **Upgrade GPU**: Ensure you are using an NVIDIA RTX series graphics card, and a model with as strong performance as possible (such as RTX 4080/4090). The GPU is the core computing unit for OrcaLab simulation and rendering.
-   **Update GPU Drivers**: Install the latest version of NVIDIA graphics drivers; new drivers often include performance optimizations and bug fixes.
-   **Upgrade CPU**: A faster CPU helps handle physics calculations, AI logic, and Python script execution.
-   **Increase Memory**: Sufficient memory prevents frequent data reads/writes to the hard drive, reducing stuttering.
-   **Use SSD/NVMe Drives**: High-speed drives can accelerate scene and asset loading speed.

#### Hardware Checks
-   `nvidia-smi`: Check GPU usage, VRAM usage, and driver version.
-   `htop`: Check CPU and memory usage.

### 2. **Optimize OrcaLab Software Configuration**

#### Measures
-   **Ensure the Latest OrcaLab Version**: Regularly upgrade the OrcaLab client and `orca-lab` package; new versions may include performance improvements.
    ```bash
    conda activate orcalab
    pip install --upgrade orca-lab
    ```
-   **Adjust Physics Engine Time Step**:
    -   Reducing the time step improves physics accuracy but reduces speed; increasing the time step improves speed but may reduce accuracy and stability.
    -   In the simulation program's configuration file or code, appropriately adjust the physics time step to find the balance between performance and accuracy.
-   **Adjust Physics Engine Iteration Count**:
    -   Reducing physics solver iterations can improve speed but may result in unsatisfied constraints or instability.
    -   This also needs to be weighed based on actual requirements.
-   **Optimize Rendering Quality**:
    -   The OrcaLab client may provide rendering settings; try lowering rendering resolution and turning off unnecessary post-processing effects (such as anti-aliasing, shadow quality).

### 3. **Manage Scene Complexity**

#### Measures
-   **Simplify 3D Models**:
    -   Use low-polygon models (Low-poly) instead of high-polygon models.
    -   Use LOD (Level of Detail) techniques for distant objects.
    -   Remove invisible or unimportant surfaces from the scene.
-   **Reduce Object Count in the Scene**:
    -   Only place necessary objects in the scene; remove irrelevant decorative elements.
    -   For background objects without physics interaction, set them as static or non-physics objects.
-   **Optimize Textures and Materials**:
    -   Use appropriately sized textures; avoid excessively large maps.
    -   Optimize material shaders and reduce the use of complex shaders.
-   **Reduce Light Count and Complexity**:
    -   Too many dynamic lights or complex lighting calculations can significantly impact performance.
    -   Try using baked lighting or reducing real-time shadows.
-   **Optimize Physics Interactions**:
    -   Reduce the number of objects simultaneously undergoing complex physics interactions in the scene.
    -   Turn off physics properties for objects that don't need physics interaction.

### 4. **Optimize Simulation Program Code**

#### Measures
-   **Efficient Python Code**: Ensure your simulation Python scripts are efficient, avoiding redundant calculations, memory leaks, or unnecessary loops.
-   **Vectorized Operations**: Use libraries like NumPy for vectorized operations to avoid slow Python-level loops.
-   **Async Programming / Multithreading**: If your simulation program includes I/O-intensive tasks, consider using async or multithreading to improve concurrency.
-   **Reduce API Call Frequency**: Minimize the frequency of data exchange between Python scripts and the OrcaLab core engine.

### 5. **System Environment Optimization**

#### Measures
-   **Close Unnecessary Background Programs**: Free up CPU, GPU, and memory resources.
-   **Adjust Power Settings**: Ensure the system is in high-performance mode, not power-saving mode.
-   **Regular System Cleaning**: Clear temporary files, old log files, etc.
-   **Ensure Sufficient Swap Space**: If physical memory is insufficient, the system may use the hard drive as swap space, which will significantly degrade performance.

## 📝 Summary

Improving OrcaLab simulation speed is a comprehensive optimization process that requires coordinated efforts at the **hardware, software, and scene** levels. Prioritize ensuring hardware configuration meets requirements, then further improve performance by optimizing OrcaLab settings, simplifying scenes, and optimizing simulation code. Regular checking and adjustment are key to maintaining a smooth simulation experience.

## Related Links
- [What hardware configuration is required to install OrcaLab?](FAQ-list/016-hardware-requirements-for-installing-orcalab.md)
- [Why does OrcaLab recommend NVIDIA RTX graphics cards?](FAQ-list/017-why-does-orcalab-recommend-nvidia-rtx-gpus.md)
- [What are the memory and storage requirements for OrcaLab?](FAQ-list/033-memory-and-storage-requirements-for-orcalab.md)
- [What is the technical architecture of OrcaLab?](FAQ-list/013-what-is-the-technical-architecture-of-orcalab.md)