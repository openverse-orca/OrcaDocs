# How to manage asset package versions?

## Question
Asset packages in the OrcaLab Asset Library typically have version updates. How can I find out about version information for asset packages? How does the OrcaLab client handle asset package version updates?

## Answer

The OrcaLab Asset Library supports version management for asset packages to ensure users can access the latest, most stable assets and understand the update history of assets. The OrcaLab client automatically handles the synchronization of asset package updates.

## 📋 Viewing Asset Package Version Information

### 1. **View on the Asset Library Webpage**

- **Asset Package Detail Page**: On the Asset Library page ([https://simassets.orca3d.cn/](https://simassets.orca3d.cn/)), click on any asset package to enter its detail page.
- **Version Notes**: On the detail page, there is typically a dedicated area displaying the asset package's **version number, update date, release notes**, and other information.



### 2. **View in the OrcaLab Client**

- **Assets Panel**: In the OrcaLab client's "Assets Panel," when hovering over an asset, the right side displays the item's name, path, **metadata**, and other information. This metadata may include the version number.
- **Client Logs**: During client startup, if asset packages are updated, the terminal or client logs may display relevant version update information.

## 🔄 Asset Package Update Mechanism

The OrcaLab client uses an automatic synchronization mechanism to manage asset package version updates:

### 1. **Automatic Update Detection**
- **Detection on Startup**: Each time the OrcaLab client starts, it automatically connects to the online Asset Library and checks whether new versions of your subscribed asset packages are available.
- **Background Checks**: Updates may also be periodically checked in the background while the client is running (though a restart is usually required to apply them).

### 2. **Download & Update**
- **Version Comparison**: If the online Asset Library's asset package version is higher than your locally downloaded version, the client automatically begins downloading the new version.
- **Overwrite Old Version**: After download is complete, the new version of the asset package overwrites the local old version. This means you always use the latest version of the asset.

### 3. **Sync Notification**
- During client startup, if asset packages need updating or downloading, a "Syncing asset packages..." message is displayed.



### 4. **Triggering Updates**
- **Restart Client**: When subscribing to or updating asset packages on the Asset Library webpage, the most reliable way to trigger an update is to **close and restart the OrcaLab client**.

## 💡 Importance of Asset Package Version Management

### 1. **Bug Fixes & Optimizations**
- Asset package updates may include fixes for model bugs, adjustments to physical properties, optimization of material textures, as well as new features or components.

### 2. **Compatibility Assurance**
- Core features of the OrcaLab client sometimes work in conjunction with specific versions of asset packages. Keeping asset packages updated ensures optimal compatibility.

### 3. **Access to Latest Content**
- Ensures you can use the latest models and scenes in the Asset Library, supporting the latest simulation tasks.

## ⚠️ Usage Notes

### 1. **Network Stability**
- Asset package updates require downloading data, so a stable network connection is necessary. Unstable networks may cause update failures or download interruptions.

### 2. **Disk Space**
- Ensure sufficient local disk space to store updated asset packages. Although they overwrite old versions, downloading new versions still requires temporary space.

### 3. **Project Compatibility**
- In the vast majority of cases, asset package updates are backward compatible. However, in rare cases, if an asset package undergoes major structural changes, it may affect your existing scene layouts. It is recommended to back up your scene files before starting important projects and test after updates.

### 4. **Forced Updates**
- OrcaLab currently does not provide a feature to manually force rollback to an older version of an asset. If you need to use a specific historical version of an asset, you may need to contact technical support or manage backups locally.

## 📝 Summary

OrcaLab manages asset package versions through an automatic synchronization mechanism, ensuring users always have the latest assets. You can view version information through the detail page on the Asset Library webpage. To apply updates, be sure to **restart the OrcaLab client** after subscribing or detecting updates.

## Related Links
- [Asset Library Basic Operation Guide](user-guide/asset-library-basic-operation-guide.md)
- [How to use subscribed assets in OrcaLab?](FAQ-list/047-how-to-use-subscribed-assets-in-orcalab.md)
- [How to unsubscribe from unwanted assets?](FAQ-list/048-how-to-unsubscribe-from-unwanted-assets.md)