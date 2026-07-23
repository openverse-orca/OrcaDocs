# How to switch between day and night scenes?

## Question
OrcaLab provides two default scene options at startup: "orcalab_day" (daytime) and "orcalab_night" (nighttime). How do I switch between these two environments? What are the differences between them?

## Answer

The day and night scene options provided by OrcaLab are designed to give users a simulation experience under different lighting conditions. These two scenes primarily differ in **lighting conditions and visual effects**, making them suitable for different testing requirements.

## 📋 Scene Switching Methods

### 1. **Select at Startup (Primary Method)**

When the OrcaLab client starts, a "Select Scene" dialog appears. This is the most direct way to switch between the default day/night scenes.

#### Steps
1.  **Launch the OrcaLab Client**:
    ```bash
    conda activate orcalab
    orcalab
    ```
2.  **Wait for Sync**: The client will display "Syncing asset packages..." — please wait for it to complete.
3.  **Select Scene**: In the "Select Scene" dialog that appears, you will see the following options:
    -   `orcalab_day` (Daytime Scene)
    -   `orcalab_night` (Nighttime Scene)
    -   `previewthumbnail_orcalab` (Thumbnail rendering, typically for preview)
    -   Plus any other scene-containing asset packages you have subscribed to.
4.  **Select Layout**: Usually choose "Load Default Layout."
5.  **Click "Open"**: After making your selection, click "Open" and OrcaLab will load your chosen scene.





### 2. **Switch Within the Client (May Require Manual Configuration)**

The OrcaLab client itself may not provide a one-click toggle between day/night scenes, as this is primarily achieved by loading different scene files.

#### Potential Approaches (Advanced Customization)
-   **Load Different Layout Files**: If your project includes different layout files for day and night, you can load them via "File" → "Open Layout."
-   **Modify Scene Lighting Properties**: In the "Edit Panel," if you can access the scene's lighting components, you can try manually adjusting lighting parameters (such as color, intensity, direction) to simulate day and night effects.
-   **Custom Script Control**: Dynamically modify scene lighting and environment parameters by writing Python scripts. This requires more in-depth development.

## 💡 Differences Between Day and Night Scenes & Their Applications

### 1. **Lighting Conditions**
-   **Daytime Scene**:
    -   **Characteristics**: Bright, typically simulating direct sunlight with strong directional lighting and clear shadows.
    -   **Uses**: Testing robot perception in well-lit environments (such as visual recognition, depth perception), evaluating grasping stability of robotic arms under complex shadows.
-   **Nighttime Scene**:
    -   **Characteristics**: Dark, low light intensity, may simulate moonlight, streetlights, or indoor lighting with soft or blurred shadows.
    -   **Uses**: Testing robot perception performance under low-light conditions, nighttime navigation capability, or evaluating identification and response to light sources (such as the robot's own lights, environmental warning lights).

### 2. **Visual Effects**
-   **Daytime Scene**: Vivid colors, prominent details, clearer overall visual effect.
-   **Nighttime Scene**: Overall darker tones, possibly with blue or orange tints to create a nighttime atmosphere, placing higher demands on detail observation.

### 3. **AI Training Data Diversity**
-   When conducting AI training (especially vision-based perception model training), using scenes with different lighting conditions can increase training data diversity, improving model generalization and robustness.

## ⚠️ Important Notes

### 1. **Subscribed Assets**
- If you have subscribed to other asset packages that contain scenes, those scenes will also appear in the "Select Scene" dialog. Their names will reflect their content or lighting characteristics.

### 2. **Performance Impact**
- Different lighting and scene complexity may affect rendering performance. Nighttime scenes may require more real-time lighting calculations or have different environment maps.

### 3. **Custom Lighting**
- In "No Simulation Program (Manual Start)" mode, you can try adding and adjusting light objects in the scene through the "Edit Panel" to achieve custom lighting effects.

## 📝 Summary

OrcaLab makes it convenient for users to quickly switch between different lighting environments by providing two default scenes — "orcalab_day" and "orcalab_night" — at startup. They differ in visual and lighting characteristics, making them suitable for testing robot perception and behavior in different environments. Advanced users can also achieve more flexible scene lighting control by modifying lighting parameters or writing scripts.

## Related Links
- [OrcaLab Basic Operation Guide](user-guide/orca-lab-basic-operation-guide-v1.0.md)
- [What are the components of the OrcaLab interface?](FAQ-list/061-what-are-the-components-of-the-orcalab-interface.md)