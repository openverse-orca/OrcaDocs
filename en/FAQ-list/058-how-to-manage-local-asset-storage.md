# How to manage local asset storage space?

## Question
Asset packages downloaded by OrcaLab occupy local hard drive space. As I subscribe to more and more assets, I may face storage space shortages. How can I effectively manage local asset storage space?

## Answer

Effectively managing local asset storage space is key to ensuring OrcaLab runs smoothly and your system stays healthy. You can optimize hard drive usage through various strategies, including **cleaning up unnecessary assets, manually deleting files, and performing regular maintenance**.

## 📋 Local Asset Storage Space Management Strategies

### 1. **Only Subscribe to Necessary Assets**

#### Strategy
- **Subscribe On Demand**: In the Asset Library, only subscribe to asset packages that you truly need for your current projects or learning phase.
- **Avoid Blind Subscription**: Do not subscribe to all asset packages at once, especially large ones.

#### How to
- On the Asset Library webpage, carefully review the asset package's "Details" to understand its content and size before deciding whether to subscribe.

### 2. **Unsubscribe from Unneeded Asset Packages**

#### Strategy
- Periodically review your "Personal Center" → "Subscribed Assets" list and unsubscribe from asset packages you no longer use.

#### How to
1. Log into the OrcaLab Asset Library ([https://simassets.orca3d.cn/](https://simassets.orca3d.cn/)).
2. Enter "Personal Center" and find "Subscribed Assets."
3. Click the "Unsubscribe" button next to asset packages you no longer need.
4. **Restart the OrcaLab Client**: This will prevent the client from syncing that asset package again on the next launch and will remove it from the client's Assets Panel.



### 3. **Manually Delete Local Asset Files (Operate with Caution)**

After unsubscribing, local asset files on your hard drive are not automatically deleted. If you need to completely free up space, you can delete them manually.

#### Strategy
- Locate the OrcaLab local asset storage directory and manually delete the files corresponding to unneeded asset packages.

#### How to
1.  **Locate the Asset Storage Path**:
    -   OrcaLab's local assets are typically stored in a hidden folder under your user home directory (such as `~/.orcalab/assets/`), or in a specific subfolder under the Conda environment's `site-packages` directory.
    -   You can find the specific asset storage path in the OrcaLab client's startup logs or "About OrcaLab" information.
    -   **Example using the `OrcaPlayground` project**: Its assets may be stored in a specific subdirectory under the project directory.
    ```bash
    # Assuming assets are stored at ~/.orcalab/assets/
    ls -lh ~/.orcalab/assets/
    ```
2.  **Confirm File Ownership**: Before deleting, **be absolutely sure that the files you want to delete indeed belong to unneeded asset packages and are not being used by any other active projects**.
3.  **Execute Deletion**:
    ```bash
    # Example: Delete a specific asset package directory
    rm -rf ~/.orcalab/assets/your_asset_package_name
    ```

#### ⚠️ **Warning: The `rm -rf` command is extremely high-risk. Be absolutely sure to confirm the path and files to avoid accidentally deleting important system files or project files in use.**

### 4. **Clean Conda and Pip Caches**

Conda and Pip cache downloaded package files on your system, and these caches can also occupy significant space. Regular cleaning can effectively free up space.

#### How to
- **Clean Conda Cache**:
  ```bash
  conda clean --all
  ```
- **Clean Pip Cache**:
  ```bash
  pip cache purge
  ```

### 5. **Optimize Hard Drive Usage**

#### Strategy
- **Use Large-Capacity SSD**: If budget allows, prioritize SSDs with larger capacity, especially NVMe SSDs, to meet growing asset demands.
- **External Storage**: For infrequently used or archived simulation data, recorded videos, and other large files, move them to external hard drives or network-attached storage (NAS).

#### How to
- Set OrcaLab's local asset storage directory to a dedicated, larger-capacity partition or drive.

## 📝 Summary

Managing local asset storage space requires **periodically reviewing subscriptions, unsubscribing from unneeded assets, carefully manually deleting files**, supplemented by measures such as **cache cleaning**. Proper storage management not only frees up valuable hard drive space but also ensures the OrcaLab runtime environment remains clean and efficient.

## Related Links
- [Asset Library Basic Operation Guide](user-guide/asset-library-basic-operation-guide.md)
- [How to unsubscribe from unwanted assets?](FAQ-list/050-how-to-unsubscribe-from-unwanted-assets.md)
- [What are the memory and storage requirements for OrcaLab?](FAQ-list/033-memory-and-storage-requirements-for-orcalab.md)