---
title: Best practices for and troubleshooting Adobe Experience Manager desktop app
description: Follow best practices and troubleshoot to resolve the occasional issues related to installation, upgrade, configuration, and so on.
uuid: ce98a3e7-5454-41be-aaaa-4252b3e0f8dd
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.5/ASSETS, SG_EXPERIENCEMANAGER/6.4/ASSETS, SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: f5eb222a-6cdf-4ae3-9cf2-755c873f397c
index: y
internal: n
snippet: y
---

# Troubleshoot Adobe Experience Manager desktop app {#troubleshoot-v2}

Adobe Experience Manager (AEM) desktop app connects to a remote Experience Manager deployment's Digital Asset Management (DAM) repository. The app fetches repository information and search results on your machine, downloads and uploads files and folders, and includes capabilities to manage conflicts with AEM Assets user interface.

Read on to troubleshoot the app, learn the best practices, and find out the limitations.

## Best practices {#best-practices-to-prevent-troubles}

Adhere to the following best practices to prevent some common issues and troubleshooting.

* **Understand how the desktop app works**: Before starting to use the application, spend a few moments knowing how the app works. Know about linking between Experience Manager web interface and desktop, repository mapping, asset caching, saving locally and uploading in background. See [how it works](release-notes.md#how-app-works).

* **Avoid unsupported characters in folder names**: Do not use whitespaces and invalid characters when creating or uploading folders. See a list of characters at [Create folders in Experience Manager Assets](https://docs.adobe.com/content/help/en/experience-manager-65/assets/managing/managing-assets-touch-ui.html#Creatingfolders). Some Adobe Experience Manager use cases may be impacted by unsupported characters in the folder name.

* **Best practices to avoid conflicts**: To avoid potential conflicts when collaborating on multiple assets, see [avoid editing conflicts](using.md#adv-workflow-collaborate-avoid-conflicts).

* **Use folder upload for large, hierarchical folders**: Instead of using the Assets web interface or other methods, use Experience Manager desktop app to upload large folders. The app uploads the assets in background with logging and monitoring. See [bulk upload assets](using.md#bulk-upload-assets).

* **Use the latest version**: Use the latest app version and always check for compatibility before installing either a new app version or before upgrading to a newer Adobe Experience Manager version. See [release notes](release-notes.md).

* **Use the same drive letter**: Use the same drive letter across an organization to map to the Adobe Experience Manager DAM. To see assets placed by other users, the paths must be the same. Using the same drive letter ensures a constant path to DAM assets. The assets remain placed and are not removed even if different drive letters are used by different users.

* **Mind the network**: Network performance is critical to Experience Manager desktop app's performance. If you face slowed response to file transfers or bulk operations, turn off the features or apps that might cause lots of network traffic.

* **Unsupported use cases for desktop app**: Do not use the app for Assets' migration (it needs planning and other tools); for heavy-duty DAM operations (like moving large folders, large uploads, finding files using advanced metadata searches); and as a sync client (design principles and usage patterns are different from in-sync clients like Microsoft OneDrive or Adobe Creative Cloud desktop sync).

* **Timeout**: Currently, desktop app does not have a configurable timeout value that disconnects the connection between Experience Manager server and desktop app after a fixed time interval. When uploading large assets, if the connection gets timeout after a while, the app retries to upload the asset a few times by increasing the upload timeout. There is no recommended way to change the default timeout settings.

## How to troubleshoot {#troubleshooting-prep}

To troubleshoot desktop app issues, be aware of the following information. Also, it prepares you to better convey the issues to Adobe Customer Care if you choose to seek support.

### Enable debug mode {#enable-debug-mode}

To troubleshoot, you can enable the debug mode and get more information in the logs. To use the app in debug mode on Mac, use the following command line options in a terminal or at the command prompt: `AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app`.

To enable debug mode on Windows, follow these steps:

1. Locate `Adobe Experience Manager Desktop.exe.config` file in your desktop app installation folder. By default, the folder is `C:\Program Files\Adobe\Adobe Experience Manager Desktop`.

1. Locate `<level value="INFO"/>` towards the end of the file. Change the value from `INFO` to `DEBUG`, which is `<level value="DEBUG"/>`. Save and close the file.

1. Locate `logging.json` file in your desktop app installation folder. By default, the folder is `C:\Program Files\Adobe\Adobe Experience Manager Desktop\javascript\`.

1. In `logging.json` file, locate all the instances of `"level": "info"`. Change the values from `info` to `debug`, which is `"level": "debug"`. Save and close the file.

1. Clear the cached directories that are at the location set in the application [Preferences](/help/install-upgrade.md#set-preferences).

1. Restart the desktop app.

<!-- The Windows command doesn't work for now.
* On Windows: `SET AEM_DESKTOP_LOG_LEVEL=DEBUG & "C:\Program Files\Adobe\Adobe Experience Manager Desktop\Adobe Experience Manager Desktop.exe"`
-->

### Location of log files {#check-log-files-v2}

You can find the log files for AEM desktop app at the following locations. When uploading many assets, if some files fail to upload, see `backend.log` file to identify the failed uploads.

* Path on Windows: `%LocalAppData%\Adobe\AssetsCompanion\Logs`

* Path on Mac: `~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`

>[!NOTE]
>
>When working with Adobe Customer Care on a support request/ticket, you may be asked to share the log files to help the Customer Care team understand the issue. Archive the entire `Logs` folder and share it with your Customer Care contact.

### Clear cache {#clear-cache-v2}

Clearing AEM desktop app's cache is a preliminary troubleshooting task that can resolve several issues. Clear the cache from the app preferences. See [set preferences](install-upgrade.md#set-preferences). The default location of the cache folder is:

* On Windows: `%LocalAppData%\Adobe\AssetsCompanion\Cache\`

* On Mac: `~/Library/Group/Containers/group.com.adobe.aem.desktop/cache/`

However, the location can change depending on AEM desktop's configured AEM endpoint. The value is an encoded version of the targeted URL. For example, if the application is targeting `http://localhost:4502`, the directory name is `http%3A%2F%2Flocalhost%3A4502%2F`. To clear the cache, delete the appropriate folder. Another reason to clear cache is to free disk space when you are running low on disk space.

>[!CAUTION]
>
>If you clear AEM desktop cache, local asset modifications that are not synced to AEM server, are irrevocably lost.

### Know the AEM desktop app version {#know-app-version-v2}

Click ![App menu](assets/do-not-localize/more_options_da2.png) to open the app's menu and click **[!UICONTROL Help]** > **[!UICONTROL About]**.

## Cannot see placed assets {#placed-assets-missing}

If you cannot see the assets that you or other creative professionals placed in the support files (say, INDD files), check the following:

* Connection to the server. Flaky network connectivity can stall asset downloads.
* File size. Large assets take longer to download and display.
* Drive letter consistency. If you or another collaborator placed the assets while mapping the AEM DAM to a different drive letter, the placed assets do not display.
* Permissions. To check if you have permissions to fetch the placed assets, contact your AEM administrator.

## Issues when upgrading on macOS {#issues-when-upgrading-on-macos}

Occasionally issues may occur when upgrading AEM desktop app on macOS. This is caused by legacy system folder for AEM desktop app preventing new versions of AEM desktop app to load correctly. To remedy this issue, the following folders and files can be manually removed.

Before executing the following steps, drag the `Adobe Experience Manager Desktop` application from the macOS Applications folder to the Trash. Then open terminal, execute the following command, and provide your password when prompted.

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

## Cannot upload files {#upload-fails}

If you are using desktop app with AEM 6.5.1 or later, upgrade S3 or Azure connector to version 1.10.4 or later. It resolves file upload failure issue related to [OAK-8599](https://issues.apache.org/jira/browse/OAK-8599). See [install instructions](install-upgrade.md#install-v2).

## SSL configuration issue {#ssl-config-v2}

The libraries that AEM desktop app uses for HTTP communication utilizes strict SSL enforcement. At times, a connection may succeed using a browser but fails using AEM desktop app. To configure SSL appropriately, install the missing intermediate certificate in Apache. See [How to install an Intermediate CA cert in Apache](https://access.redhat.com/solutions/43575).

## App is unresponsive {#unresponsive}

Rarely the application may become unresponsive, display just a white screen, or display an error at the bottom of the interface without any options on the interface. Try the following in the order:

* Right click on the application interface and click **[!UICONTROL Refresh]**.
* Exit the application and open it again.

In both methods, the app starts at the root DAM folder.

>[!MORELIKETHIS]
>
>* [Known issues](release-notes.md#known-issues-v2)
>* [Avoid editing conflicts](using.md#adv-workflow-collaborate-avoid-conflicts)
