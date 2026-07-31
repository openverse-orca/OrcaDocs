# What to do if Asset Library access is slow?

## Question
When using the OrcaLab Asset Library, I find the access speed to be very slow — browsing, searching, and subscribing to assets are all sluggish. How can I optimize Asset Library access speed?

## Answer

Slow OrcaLab Asset Library access speed is typically related to your **network environment, network configuration, server load, or local cache**. Through a series of troubleshooting and optimization measures, you can significantly improve your Asset Library access experience.

## 📋 Slow Asset Library Access Troubleshooting & Optimization

### 1. **Check Network Connection Quality (Primary Check)**

#### Symptoms
-   Web pages load slowly, images don't fully display.
-   Subscribe or unsubscribe operations have long delays with no response.
-   Asset package download speed is very slow.

#### Solutions
-   **Test Network Speed**: Use an online speed test tool (such as [Speedtest.net](https://www.speedtest.net/)) to test your network bandwidth and latency.
-   **Test Asset Library Server Connectivity**:
    ```bash
    ping simassets.orca3d.cn
    traceroute simassets.orca3d.cn # View network path and latency
    ```
-   **Check Wi-Fi Signal or Network Cable**: Ensure good Wi-Fi signal, or use a wired connection for more stable networking.
-   **Restart Router/Modem**: Network devices running for extended periods may experience performance degradation.
-   **Switch Network Environment**: If possible, try switching to another network (such as a mobile hotspot, other broadband) to see if there is improvement.

### 2. **Optimize Network Configuration**

#### Symptoms
-   Slow in specific network environments; normal in others.
-   Possible slow DNS resolution issues.

#### Solutions
-   **Configure DNS Servers**: Try setting your DNS servers to public, faster DNS services (such as Google DNS: `8.8.8.8` and `8.8.4.4`, or Cloudflare DNS: `1.1.1.1` and `1.0.0.1`).
    -   In Ubuntu, you can configure this by modifying `/etc/resolv.conf` or through network settings.
-   **Check Proxy Settings**: If you are using a proxy, ensure the proxy server is stable and responsive. Unnecessary proxies may slow down speed.

### 3. **Browser Optimization**

#### Symptoms
-   Asset Library webpage is laggy and loads slowly.

#### Solutions
-   **Clear Browser Cache and Cookies**: Excessive cache may degrade browser performance.
-   **Disable Unnecessary Browser Extensions**: Certain extensions may interfere with webpage loading.
-   **Update Your Browser**: Ensure your browser is the latest version for optimal webpage rendering performance.
-   **Try Other Browsers**: Try accessing the Asset Library with a different browser to rule out browser compatibility issues.

### 4. **Server Load Issues**

#### Symptoms
-   All users generally report slow Asset Library access.
-   Lag occurs not during specific time periods.

#### Solutions
-   **Check Official Announcements**: Visit the OrcaLab official website or community forum to see if there are announcements about Asset Library server maintenance or high load.
-   **Avoid Peak Hours**: If server load is the main cause, try accessing the Asset Library during off-peak hours.

### 5. **Local Cache Issues**

#### Symptoms
-   Asset synchronization lags when the OrcaLab client starts.

#### Solutions
-   **Clear OrcaLab Local Cache**: The OrcaLab client may store some cached data locally. Try cleaning these caches, typically located in hidden folders under your user home directory (such as `~/.orcalab/` or `~/.cache/orcalab/`).
    -   **Note**: This operation may require you to log in again or re-sync some data.

### 6. **OrcaLab Client Version Issues**

#### Symptoms
-   The client is always slow when syncing assets.

#### Solutions
-   **Upgrade the OrcaLab Client**: Ensure your OrcaLab client is the latest version; newer versions may include optimizations to the asset sync mechanism.
    ```bash
    conda activate orcalab
    pip install --upgrade orca-lab
    ```

## 💡 Best Practices

-   **Regular Maintenance**: Regularly clear browser cache, check network connectivity, and update software versions.
-   **Subscribe On Demand**: Only subscribe to the assets you truly need to reduce the amount of data the client needs to sync.
-   **Prioritize Wired Connections**: If possible, use a wired network connection, which is typically more stable and faster than wireless.

## 📝 Summary

The causes of slow Asset Library access are diverse but mainly focus on network, local configuration, and server load. By **optimizing the network environment, clearing caches, updating software**, and **checking official announcements**, you can typically resolve this issue effectively.

## Related Links
- [Asset Library Basic Operation Guide](user-guide/asset-library-basic-operation-guide.md)
- [How to search and subscribe to assets?](FAQ-list/045-how-to-search-and-subscribe-to-assets.md)
- [What to do if asset download fails?](FAQ-list/055-what-to-do-if-asset-download-fails.md)