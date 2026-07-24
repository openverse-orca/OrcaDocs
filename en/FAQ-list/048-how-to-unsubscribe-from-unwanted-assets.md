# How to unsubscribe from unwanted assets?

## Question
I have subscribed to some asset packages in the OrcaLab Asset Library, but some are no longer needed, or I want to free up space for new projects. How can I unsubscribe from these no-longer-needed asset packages?

## Answer

Unsubscribing from OrcaLab asset packages is a simple process that you can do through the Asset Library's "Personal Center." After unsubscribing, the OrcaLab client will no longer sync these assets on the next launch and will remove them from the local asset list (though local files may still need manual cleanup).

## 📋 Asset Unsubscription Process

### Step 1: Log into the OrcaLab Asset Library

Open your web browser and visit the OrcaLab Asset Library page:

[https://simassets.orca3d.cn/](https://simassets.orca3d.cn/)

And log in with your OrcaLab account.

### Step 2: Enter "Personal Center"

After logging in, find and click "Personal Center" in the left navigation bar of the Asset Library page.



### Step 3: Navigate to "Subscribed Assets"

On the "Personal Center" page, you will see a "Subscribed Assets" (or similarly named) list. Click to enter, and you will see all the asset packages you are currently subscribed to.

### Step 4: Select the Asset Package to Unsubscribe From

- Find the asset package you wish to unsubscribe from in the "Subscribed Assets" list.
- Typically, there is an "Unsubscribe" button/link next to each asset package.



### Step 5: Confirm Unsubscription

- After clicking "Unsubscribe," the system may display a confirmation dialog asking if you are sure you want to unsubscribe. Please read the prompt carefully.
- After confirming, the asset package will be removed from your "Subscribed Assets" list.

### Step 6: Restart the OrcaLab Client (Important)

- After unsubscribing on the Asset Library webpage, you must **close and restart the OrcaLab client**. The client will automatically detect subscription changes on startup:
  ```bash
  # Exit the OrcaLab client (if running)
  # Then restart
  conda activate orcalab
  orcalab
  ```
- The client will no longer sync that asset package and will remove it from the local "Assets Panel."

## 💡 Effects of Unsubscribing

### 1. **No More Automatic Sync**
- The OrcaLab client will no longer download or update that asset package from the cloud on startup.

### 2. **Removal from Client Assets Panel**
- All assets in that package will no longer appear in the OrcaLab client's "Assets Panel," and you will not be able to drag and drop them for use in the client.

### 3. **Local File Handling**
- **Typically, unsubscribing** does **not automatically delete** the already-downloaded asset files on your local hard drive. These files remain in your OrcaLab local asset storage directory.
- If you need to completely free up disk space, you may need to **manually delete** these local files. The specific asset storage path can be found in OrcaLab's configuration files or logs, or is typically located in a specific subfolder under the Conda environment's `site-packages` directory, or in paths like `~/.orcalab/assets/` under your user home directory.

## ⚠️ Important Notes

### 1. **Operate with Caution**
- After unsubscribing, if you need to use that asset package again in the future, you will need to re-subscribe and re-download.

### 2. **Project Dependencies**
- If your existing projects or scenes are using assets from a particular asset package, do not casually unsubscribe. Unsubscribing may cause your project to fail to load or display abnormally.
- Before unsubscribing, ensure that the assets in that package are no longer in use by any active projects.

### 3. **AI-Generated Assets**
- If you unsubscribe from an asset package that contains assets you generated via AI, those AI-generated assets will also no longer appear in the client. However, AI generation records are typically retained in your Personal Center.

## 📝 Summary

Unsubscribing from OrcaLab asset packages can be done through the Asset Library's "Personal Center." The operation is simple, but be sure to **restart the OrcaLab client** to sync the changes. Also, note that unsubscribing does not automatically delete local files; manually clean them up if needed, and confirm that existing projects will not be affected.

## Related Links
- [Asset Library Basic Operation Guide](user-guide/asset-library-basic-operation-guide.md)
- [How to search and subscribe to assets?](FAQ-list/045-how-to-search-and-subscribe-to-assets.md)
- [How to use subscribed assets in OrcaLab?](FAQ-list/047-how-to-use-subscribed-assets-in-orcalab.md)