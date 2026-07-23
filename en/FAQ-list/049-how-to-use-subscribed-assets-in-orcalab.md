# How to use subscribed assets in OrcaLab?

## Question
I have successfully subscribed to 3D asset packages in the OrcaLab Asset Library. How can I find these assets in the OrcaLab client and add them to my simulation scene?

## Answer

Once you subscribe to asset packages in the OrcaLab Asset Library, the OrcaLab client will automatically sync these assets to your local machine. You can find them in the client's "Assets Panel" and drag them into your simulation scene.

## 📋 Using Subscribed Assets in the OrcaLab Client

### Step 1: Ensure Assets Are Synced Locally

1.  **Restart the OrcaLab Client**: After subscribing to assets on the Asset Library webpage, you must **close and restart the OrcaLab client** to trigger asset download and synchronization.
    ```bash
    # Activate the OrcaLab Conda environment
    conda activate orcalab
    # Launch OrcaLab
    orcalab
    ```
2.  **Observe the Sync Process**: The client will display a "Syncing asset packages..." message during startup. Please wait for this process to complete to ensure assets have been successfully downloaded.



### Step 2: Open the OrcaLab Client Interface

After successfully launching and syncing assets, you will enter the OrcaLab GUI.



### Step 3: Navigate to the "Assets Panel"

-   At the bottom of the OrcaLab client interface (or according to your layout settings), find and click the "Assets" tab to enter the "Assets Panel" module.



### Step 4: Search or Browse for the Required Asset

-   **Search Function**: Enter the asset name keyword in the search box at the top of the Assets Panel to quickly filter and find downloaded assets.
-   **Browse Function**: The Assets Panel displays all your subscribed and downloaded assets in a list or grid format. You can scroll to browse.

### Step 5: Drag the Asset into the Viewport

-   **Drag Operation**: Once you find the asset you want to use, click on it with your mouse and **drag it to the central "Viewport" area** (the 3D scene).
-   **Placement**: Release the mouse in the viewport, and the asset will appear in the scene.

### Step 6: Adjust the Asset's Transform Properties

-   **Select the Asset**: Click on the asset you just placed in the "Viewport," or select the asset in the "Outline Panel."
-   **Edit Properties**: In the right-side "Edit Panel," you can adjust the asset's:
    -   `Position`: X, Y, Z coordinates
    -   `Rotation`: X, Y, Z axis rotation angles
    -   `Uniform Scale`: Overall scale ratio



### Step 7: Save the Scene Layout (Optional)

-   If you are satisfied with the scene setup and asset placement, it is recommended to use the "File" menu and select "Save Layout" or "Save As" to save the current scene configuration as a layout file (typically a `.json` or `.orcalab` file).
-   This way, you can directly load this layout file next time without rebuilding the scene.

## 💡 Usage Notes

### 1. **Subscription Status & Local Files**
- The OrcaLab client will only attempt to sync and download assets that have been **successfully subscribed** to in the Asset Library.
- Even if asset files exist locally, the client may not display them in the Assets Panel if they are not subscribed.

### 2. **Asset Package Types**
- Some asset packages may carry a `Scene` tag, meaning they come with a pre-configured scene layout. After subscribing to such assets, you can directly select the scene provided by that asset package in the "Select Scene" dialog when OrcaLab starts.

### 3. **Network & Disk Space**
- Ensure a good network connection during asset synchronization.
- Ensure sufficient local disk space to store downloaded asset packages.

### 4. **Asset Search Accuracy**
- When searching in the Assets Panel, if the asset name is long or contains special characters, try using partial keywords.

## 📝 Summary

OrcaLab provides a seamless asset usage workflow: subscribe on the Asset Library webpage, restart the client for automatic sync, then drag and drop from the client's "Assets Panel" and fine-tune through the "Edit Panel." Mastering this workflow is the foundation for efficiently building simulation scenes.

## Related Links
- [Asset Library Basic Operation Guide](user-guide/asset-library-basic-operation-guide.md)
- [How to search and subscribe to assets?](FAQ-list/047-how-to-search-and-subscribe-to-assets.md)
- [OrcaLab Basic Operation Guide](user-guide/orca-lab-basic-operation-guide-v1.0.md)