# What to do if asset download fails?

## Question
When starting the OrcaLab client, if asset package downloads fail or the sync process gets stuck, how should I troubleshoot and resolve this issue?

## Answer

Asset package download failures or sync getting stuck are issues that may occur when using OrcaLab, typically related to **network connectivity, disk space, Conda environment configuration, or OrcaLab client state**. Below are detailed troubleshooting steps and solutions.

## 📋 Asset Download Failure Troubleshooting & Solutions

### 1. **Check Network Connection (Most Common Cause)**

#### Symptoms
-   Client is stuck on "Syncing asset packages..." with no progress for a long time.
-   Terminal or client logs show "Connection timed out," "Network unreachable," or similar errors.

#### Solutions
-   **Test Network Connectivity**:
    ```bash
    ping simassets.orca3d.cn # Test Asset Library server connectivity
    ping www.baidu.com       # Test public network connectivity
    ```
-   **Check Firewall & Proxy**:
    -   Confirm your firewall is not blocking OrcaLab from accessing external networks. If using a proxy, ensure proxy settings are correct.
    -   If on a corporate or school network, you may need to contact the network administrator.
-   **Switch Network Environment**: Try switching to a more stable, higher-bandwidth network, such as switching from Wi-Fi to wired, or using a different hotspot.
-   **Restart Network Devices**: Restart your router and modem.

### 2. **Check for Insufficient Disk Space**

#### Symptoms
-   Client reports "No space left on device" or similar errors.
-   Download progress stops but the network is working normally.

#### Solutions
-   **Check Available Disk Space**:
    ```bash
    df -h  # View your disk partitions and available space
    ```
-   **Free Up Disk Space**:
    -   Delete unnecessary files.
    -   Clean old Conda environment cache: `conda clean --all`.
    -   If you previously downloaded other unused asset packages, you can manually delete the old local asset files (specific paths may be at `~/.orcalab/assets/` or specific directories under the Conda environment).

### 3. **OrcaLab Client State Issues**

#### Symptoms
-   Client is frozen and unresponsive.
-   Sync cannot complete even with normal network and disk.

#### Solutions
-   **Force Close and Restart the Client**:
    -   If the client is frozen, you may need to force-close the terminal window or use the system task manager to end the OrcaLab process.
    -   Then, restart OrcaLab:
        ```bash
        conda activate orcalab
        orcalab
        ```
-   **Check Logs**: Carefully review the terminal output logs during startup; they may contain more detailed error information.

### 4. **Conda Environment Issues**

#### Symptoms
-   Assets won't download even though the client starts normally.
-   Terminal reports Python or Conda environment-related errors.

#### Solutions
-   **Reactivate Conda Environment**:
    ```bash
    conda deactivate
    conda activate orcalab
    ```
-   **Check Python Dependencies**: Ensure `pip show orca-lab` shows the package is properly installed with no missing dependencies.
-   **Clean Conda Cache**: `conda clean --all`.

### 5. **Asset Library Server Issues**

#### Symptoms
-   Network is normal but unable to connect to the Asset Library for a long time.
-   There may be an official announcement indicating server maintenance.

#### Solutions
-   **Check Official Announcements**: Visit the OrcaLab official website or community forum to see if there are any server maintenance or outage announcements.
-   **Try Again Later**: If it's a server issue, you can only wait for the official fix.

## 💡 Preventive Measures

### 1. **Ensure Stable Network**
- When launching OrcaLab for asset synchronization, try to choose a stable network environment with sufficient bandwidth.

### 2. **Regularly Check Disk Space**
- Develop the habit of regularly checking and cleaning disk space, especially the project directory and OrcaLab's local asset storage directory.

### 3. **Keep Software Updated**
- Keeping the OrcaLab client and Python packages in the Conda environment up to date can reduce download failures caused by compatibility issues.

### 4. **Only Subscribe to Necessary Assets**
- Avoid subscribing to too many asset packages; only download the assets needed for your current projects or learning to reduce sync time and disk usage.

## 📝 Summary

Asset download failures are typically due to network and disk space issues. They can be effectively resolved through **checking network connectivity, ensuring sufficient disk space, and force-restarting the client**. If problems persist, document the error information in detail and contact technical support.

## Related Links
- [Asset Library Basic Operation Guide](user-guide/asset-library-basic-operation-guide.md)
- [How to search and subscribe to assets?](FAQ-list/045-how-to-search-and-subscribe-to-assets.md)
- [Why does OrcaLab auto-install dependencies on first launch?](FAQ-list/023-why-does-orcalab-auto-install-dependencies-on-first-launch.md)
- [What are the common reasons for OrcaLab startup failure?](FAQ-list/026-common-reasons-for-orcalab-startup-failure.md)