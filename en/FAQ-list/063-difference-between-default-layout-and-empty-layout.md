# What is the difference between default layout and empty layout?

## Question
When starting OrcaLab, in addition to selecting a scene, I also need to choose "Load Default Layout" or "Empty Layout." What is the difference between these two layout options? How should I choose?

## Answer

When the OrcaLab client starts, the "Layout Options" after selecting a scene determine the initial placement of objects in the 3D viewport. **Default Layout** and **Empty Layout** provide users with different starting points for scene building to accommodate various usage needs.

## 📋 Layout Options Explained

### 1. **Load Default Layout**

#### Meaning
-   When you select "Load Default Layout," OrcaLab loads **the scene layout preset for the current scene, complete with interactive objects and initial configuration**.
-   This means the scene contains not only the environmental background but also some pre-placed 3D models (such as robots, props, obstacles, etc.) with their initial positions, poses, and physical properties.

#### Applicable Scenarios
-   **Quick Simulation Start**: Run or observe preset simulation tasks immediately without manual setup.
-   **Experience Examples**: In the various quick-start or teaching examples provided by OrcaLab, selecting the default layout lets you immediately experience the preset interactive content.
-   **Learning & Reference**: Analyze how objects are placed and configured in the preset layout as a reference for building your own scenes.
-   **Scene-Containing Asset Packages**: If the asset package you subscribed to carries a "Scene" tag, loading the default layout typically loads the scene preset by the asset package author.

#### Example Effect


#### Advantages
-   **Convenience**: Saves the user time from manually placing and configuring objects.
-   **Completeness**: Provides a complete, immediately runnable simulation environment.

### 2. **Empty Layout**

#### Meaning
-   When you select "Empty Layout," OrcaLab loads **a clean scene without any preset objects**.
-   The scene only has the environment (such as ground, skybox). You can start from scratch and manually add and place 3D assets according to your needs.

#### Applicable Scenarios
-   **Custom Scene Building**: When you need to fully independently design and build a unique simulation environment.
-   **Projects from Scratch**: New projects requiring a fresh scene configuration.
-   **Avoid Interference**: When you don't want preset objects to affect your experiment or design.
-   **Performance Testing**: Test baseline performance in an empty scene or gradually add objects to observe performance changes.

#### Example Effect


#### Advantages
-   **High Degree of Freedom**: Users can fully control every element in the scene.
-   **Cleanliness**: Provides a clean canvas with no interference.

## 💡 How to Choose a Layout

### 1. **First-Time Use or Learning**
-   **Recommend "Load Default Layout"**: Quickly understand OrcaLab's features and operations through the default layout, and experience preset simulation tasks. For example, when running the four-wheel chassis car simulation, selecting the default layout lets you quickly see the car model.

### 2. **Building New Projects or Custom Scenes**
-   **Recommend "Empty Layout"**: Once you have some familiarity with OrcaLab and need to create your own simulation environment, choosing the empty layout allows you to freely build from scratch.

### 3. **Subscribed Asset Packages**
-   If the subscribed asset package carries a "Scene" tag and you want to experience the complete scene designed by the asset package author, select "Load Default Layout."
-   If you only want to use models from the asset package without its preset scene, select "Empty Layout" and then manually drag assets into the scene.

## ⚠️ Important Notes

### 1. **No Difference for Default Scenes**
- For OrcaLab's three built-in default scenes (`orcalab_day`, `orcalab_night`, `previewthumbnail_orcalab`), "Load Default Layout" and "Empty Layout" may have **no significant difference initially**, as these scenes themselves may be relatively sparse or only contain basic environments.
- **The core difference is reflected in subscribed asset packages**: If you subscribe to asset packages carrying a "Scene" tag, selecting the default layout will load the complete scene preset in that asset package.

### 2. **Layout Modification & Saving**
- Regardless of which initial layout you choose, you can modify it in the OrcaLab client.
- Modified layouts can be saved as custom layout files via "File" → "Save Layout" or "Save As" for easy loading next time.

## 📝 Summary

"Load Default Layout" provides a preset, complete scene with interactive objects, suitable for quick experience and learning; while "Empty Layout" provides a clean canvas, suitable for users to customize scenes from scratch. Choosing the appropriate layout option based on your usage purpose will significantly improve work efficiency.

## Related Links
- [OrcaLab Basic Operation Guide](user-guide/orca-lab-basic-operation-guide-v1.0.md)
- [How to switch between day and night scenes?](FAQ-list/062-how-to-switch-between-day-and-night-scenes.md)
- [How to use subscribed assets in OrcaLab?](FAQ-list/049-how-to-use-subscribed-assets-in-orcalab.md)