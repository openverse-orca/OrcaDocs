# How to use the AI 3D asset generation feature?

## Question
How do I use the "AI Asset Generation" tool in the OrcaLab Asset Library? What are the differences between Text-to-3D and Image-to-3D, and what are the usage notes and limitations?

## Answer

The OrcaLab Asset Library has a built-in powerful "AI Asset Generation" tool that allows users to quickly generate USDZ-format 3D models through **text descriptions (Text-to-3D)** or **image references (Image-to-3D)**. This greatly lowers the barrier to 3D asset creation.

## 📋 AI 3D Asset Generation Overview

### Access Entry
- In the OrcaLab Asset Library page ([https://simassets.orca3d.cn/](https://simassets.orca3d.cn/)), click "Tool Center" in the left navigation bar, then select "AI Asset Generation Tool."

### Generation Process
1.  Choose generation method: Image Reference (Image-to-3D) or Text Description (Text-to-3D).
2.  Provide input: Upload an image or enter a text description.
3.  Configure parameters (optional): Adjust generation parameters.
4.  Start generation: Click "Start Generating Asset."
5.  Wait for results: Do not refresh the page during generation.
6.  Preview & Upload: Preview the generated result and upload to Personal Center if satisfied.

## 🚀 Two Generation Methods

### 1. **Image-to-3D (Image Reference)**
- **Principle**: Based on the 2D image you upload, AI analyzes its shape, color, texture, and other features and attempts to generate a similar 3D model.
- **Best For**: When you have a specific object photo or reference image and want to quickly convert it into a 3D model.
- **How to**:
  1. Select the "Image Reference" option.
  2. Click the upload image area and select a local image file.
  3. (Optional) Adjust generation parameters.
  4. Click "Start Generating Asset."


### 2. **Text-to-3D (Text Description)**
- **Principle**: Based on the natural language text description you provide, AI understands the semantics and creatively generates a 3D model matching the description.
- **Best For**: When you have a concept in mind but no specific image, or when you want to generate an original design.
- **How to**:
  1. Select the "Text Description" option.
  2. Enter a detailed description of the 3D model in the text box, such as "a red round table" or "a yellow car with four wheels."
  3. (Optional) Adjust generation parameters.
  4. Click "Start Generating Asset."



## ⚙️ Generation Parameter Descriptions

During generation, you can adjust some parameters to influence the results. These are typically at the bottom of the AI generation interface.

-   **Separate Mesh**:
    -   **Function**: Controls whether to split a model's mesh into multiple independent model files or assets.
    -   **Use Case**: When the generated model consists of multiple independent parts and you want each part to be individually operable.
-   **Automatic Level of Detail (LOD)**:
    -   **Function**: Automatically generates multi-level detail meshes for the model. When far from the camera, lower-detail models are displayed to improve rendering performance.
    -   **Use Case**: Suitable for large complex scenes requiring performance optimization.
-   **Smooth Mesh**:
    -   **Function**: Applies smoothing to the model's mesh surface, reducing jaggedness and sharp edges.
    -   **Use Case**: Makes the model look rounder and more natural.
-   **Smoothness Intensity**:
    -   **Function**: Controls the degree of "Smooth Mesh" processing; works together with the "Smooth Mesh" parameter.
    - **Use Case**: Higher values produce more pronounced smoothing.
-   **Use Hub CLI**:
    -   **Function**: Specifies using the Hub command-line tool for model processing (i.e., AP processing).
    - **Use Case**: Usually keep the default unless you have specific technical requirements.

## ⚠️ Usage Notes & Limitations

### 1. **Daily Generation Limit**
- **Quota**: Currently, each user has **5** usage attempts per day for each method ("Image Reference" and "Text Description").
- **Reset**: Usage count resets at midnight daily.
- **Note**: Failed generations typically do not count toward the quota.

### 2. **Do Not Refresh During Generation**
- After clicking "Start Generating Asset," the page enters the generation state. Please **do not refresh the page**, as this may interrupt the generation process and lose results.

### 3. **Result Uncertainty**
- AI generation involves some randomness and creativity; results may not 100% match expectations.
- Try generating multiple times or adjusting descriptions/images to get more satisfactory results.

### 4. **Generated Model Format**
- Currently, generated models are in **USDZ** format.

### 5. **Upload to Personal Center**
- Generated models are first previewed on the page. If satisfied, you need to click the "Upload Asset" button to save them to your Personal Center, after which you can subscribe and use them in OrcaLab.



### 6. **Non-Commercial Restrictions**
- All assets created through the AI generation tool are subject to OrcaLab's **non-commercial use terms**. They must not be used for any commercial purpose.

## 💡 Tips for Improving Generation Results

### Text-to-3D Tips
- **Specific Descriptions**: Provide detailed shape, color, material, size, and function descriptions.
  - **Poor Example**: "table"
  - **Good Example**: "a red round wooden small table with three thin legs"
- **Keywords**: Use more precise keywords, such as "industrial robot" instead of "robot."
- **Iterate**: Based on the first generation result, adjust the description and generate again.

### Image-to-3D Tips
- **High-Quality Images**: Upload clear, high-resolution reference images.
- **Prominent Subject**: The subject of the 3D model in the image should be clearly visible; the background should be as clean as possible.
- **Multi-Angle Reference**: If possible, provide reference images from different angles. While only one can be uploaded currently, you can mention other angles in the description.
- **Even Lighting**: Avoid overexposure or underexposure to ensure model details are visible.

## 📝 Summary

OrcaLab's AI 3D asset generation feature is a powerful and convenient tool that allows users to quickly obtain needed assets without 3D modeling skills. Understanding its operation workflow, parameter settings, and usage limitations, and mastering some tips to improve generation results, will help you use this feature more efficiently.

## Related Links
- [Asset Library Basic Operation Guide](user-guide/asset-library-basic-operation-guide.md)
- [How to search and subscribe to assets?](FAQ-list/045-how-to-search-and-subscribe-to-assets.md)
- [Is OrcaLab free to use? What are the limitations?](FAQ-list/004-is-orcalab-free-to-use-and-what-are-the-limitations.md)