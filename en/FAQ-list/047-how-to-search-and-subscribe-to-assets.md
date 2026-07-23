# How to search and subscribe to assets?

## Question
In the OrcaLab Asset Library, how can I efficiently find the 3D assets I need? Once found, how do I subscribe to these assets so I can use them in the OrcaLab client?

## Answer

OrcaLab's Asset Library provides convenient search and subscription features to help users quickly obtain the 3D assets they need and integrate them into simulation environments.

## 🔍 Asset Search Process

### Step 1: Access the Asset Library Page

Open your web browser and visit the OrcaLab Asset Library page:

[https://simassets.orca3d.cn/](https://simassets.orca3d.cn/)

### Step 2: Choose a Search Method

The Asset Library provides two main search methods:

#### 1. **Text Description Search (Keyword Search)**
- **Features**: Find assets by entering keywords.
- **How to**:
  1. Enter the keywords for the asset you want to find in the search bar on the Asset Library page, such as "robotic arm", "table", "drone", etc.
  2. Press Enter or click the search button.
- **Tips**:
  - Try different keyword combinations, such as "UR5 robotic arm", "industrial robot".
  - Use the category filter (e.g., Industrial Assets, Robot Assets) in combination with keyword search.



#### 2. **Image Reference Search (Search by Image)**
- **Features**: Upload a reference image and the system will intelligently match similar 3D assets based on the image content.
- **How to**:
  1. Find the image search entry (usually an icon next to the search bar).
  2. Upload an image of the 3D asset you are looking for.
  3. The system will analyze and display matching results.
- **Tips**:
  - Choose images that are clear, with the target object prominent and the background clean.
  - The image should showcase as many features of the target asset as possible.



### Step 3: Filter and Sort Results

- **Category Filtering**: Use the asset categories on the left (Industrial Assets, Living Assets, etc.) to narrow down the search scope.
- **Sorting**: You can choose to sort search results by "Name" or "Size" to more quickly find the target asset.

## 📦 Asset Subscription Process

Once you find the desired asset package, you need to subscribe to it to use it in the OrcaLab client.

### Step 1: View Asset Package Details

- In the search results, click on the asset package you're interested in to enter its detail page. Here you'll see basic information, asset description, version notes, and the specific asset files included.



### Step 2: Click the "Subscribe" Button

- On the asset package detail page, find and click the "Subscribe" button.



### Step 3: OrcaLab Client Auto-Sync

- After successful subscription, the OrcaLab client will automatically detect and download the asset package on its **next launch**.
  ```bash
  # After subscribing, you need to restart the OrcaLab client to trigger the download
  conda activate orcalab
  orcalab
  ```
- The client will display a "Syncing asset packages..." message during startup.



### Step 4: Use Assets in the OrcaLab Client

- Once the asset package download is complete, you can find and use these assets in the **Assets Panel** of the OrcaLab client interface. Simply drag an asset into the viewport area to add it to the scene.



## 💡 Subscription & Usage Notes

### 1. **Account Login**
- You must be logged into your OrcaLab account to subscribe to assets.

### 2. **Network Connection**
- Subscribing to and downloading assets requires a stable network connection.
- Asset packages are typically large; ensure sufficient network bandwidth.

### 3. **Disk Space**
- Ensure your local hard drive has enough space to store downloaded asset packages.

### 4. **Restart Client**
- **Very Important**: After subscribing to or unsubscribing from assets on the Asset Library webpage, you must **close and restart the OrcaLab client** to trigger the download, update, or removal of assets.

### 5. **Personal Center**
- Subscribed asset packages are automatically synced to your "Personal Center" → "Subscribed Assets" list for easy management.

## 📝 Summary

OrcaLab's asset search functionality is powerful and flexible, supporting both text and image search methods. The subscription process is also very simple — just click a button, then restart the client for automatic synchronization. Mastering these operations will help you efficiently utilize Asset Library resources and accelerate simulation project development.

## Related Links
- [Asset Library Basic Operation Guide](user-guide/asset-library-basic-operation-guide.md)
- [What is the Asset Library and how to use it?](FAQ-list/046-what-is-the-asset-library-and-how-to-use-it.md)
- [Why does OrcaLab auto-install dependencies on first launch?](FAQ-list/023-why-does-orcalab-auto-install-dependencies-on-first-launch.md)