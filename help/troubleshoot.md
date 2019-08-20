---
title: Troubleshoot AEM desktop app
seo-title: Troubleshoot AEM desktop app for AEM Assets
description: Troubleshoot AEM desktop app to resolve the occasional issues related to installation, upgrade, configuration, and so on.
seo-description: Troubleshoot AEM desktop app to resolve the occasional issues related to installation, upgrade, configuration, and so on.
uuid: ce98a3e7-5454-41be-aaaa-4252b3e0f8dd
contentOwner: asgupta
content-strategy: redirect-pointer
content-type: troubleshooting
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
discoiquuid: f5eb222a-6cdf-4ae3-9cf2-755c873f397c
index: y
internal: n
snippet: y
---

# Troubleshoot AEM desktop app {#troubleshoot-v2}

Adobe Experience Manager (AEM) desktop app connects to a remote AEM deployment's Digital Asset Management (DAM) repository. The app fetches repository information and search results on your machine, downloads and uploads files and folders, and includes capabilities to manage conflicts with AEM Assets user interface.

Read on to troubleshoot the app, learn the best practices, and find out the limitations.

## Best practices {#best-practices-to-prevent-troubles}

Adher to the following best practices to prevent some common issues and troubleshooting.

* **Understand how the desktop app works**: Before starting to use the application, spend a few minutes knowing how the app works. Know about linking between Web UI and desktop, repository mapping, asset caching, saving locally and uploading in background. See [how it works](release-notes.md#how-app-works).

* **Best practices to avoid conflicts**: To avoid potential conflicts when collaborating on multiple assets, see [avoid editing conflicts](using.md#adv-workflow-collaborate-avoid-conflicts).

* **Use folder upload for large, hierarchical folders**: Instead of using the Assets web interface or other methods, use AEM desktop app to upload large folders. The app uploads the assets in background with logging and monitoring. See [bulk upload assets](using.md#bulk-upload-assets).

* **Use the latest version**: Use the latest app version and always check for compatbility before installing either a new app version or before upgrading to a newer AEM version. See [release notes](release-notes.md).

* **Mind the network**: Network performance is critical to AEM desktop app's performance. If you face slowed response to file transfers or bulk operations, turn off the features or apps that might cause lots of network traffic.

* **Unsupported use cases for desktop app**: Do not use the app for Assets' migration (it needs planning and other tools); for heavy-duty DAM operations (like moving large folders, large uploads, finding files using advanced metadata searches); and as a sync client (design principles and usage patterns are different than in-sync clients like Microsoft OneDrive or Adobe Creative Cloud desktop sync).

## Enable debug mode {#enable-debug-mode}

To troubleshoot, you can enable the debug mode and get more information in the logs. To run the app in debug mode, use the following command line options in a terminal or at the command prompt.

* On Windows: `SET AEM_DESKTOP_LOG_LEVEL=DEBUG & "C:\Program Files\Adobe\Adobe Experience Manager Desktop\Adobe Experience Manager Desktop.exe"`

* On Mac: `AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app`

## Check log files {#check-log-files-v2}

You can find the log files for AEM desktop app at the following locations. When uploading many assets, if some files fail to upload, see `backend.log` file at the above location to identify the failed uploads.

* On Windows: `%LocalAppData%\Adobe\AssetsCompanion\Logs`

* On Mac: `~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`

>[!NOTE]
>
>When working with Adobe Customer Care on a support request/ticket, you may be asked to share the log files to help the support team understand the issue. Archive the entire `Logs` folder and share it with the customer care.

## Clear cache {#clear-cache-v2}

Clearing AEM desktop app's cache is a preliminary troubleshooting task that can resolve several issues. Clear the cache from the app preferences. See [set preferences](install-upgrade.md#set-preferences). The default location of the cache folder is:

* On Windows: `%LocalAppData%\Adobe\AssetsCompanion\Cache\`

* On Mac: `~/Library/Group/Containers/group.com.adobe.aem.desktop/cache/`

However, the location can change depending on AEM desktop's configured AEM endpoint. The value is an encoded version of the targeted URL. For example, if the application is targeting `http://localhost:4502`, the directory name is `http%3A%2F%2Flocalhost%3A4502%2F`. To clear the cache, delete the appropriate folder. Another reason to clear cache is to free disk space when you are running low on disk space.

>[!CAUTION]
>
>If you clear AEM desktop cache, local asset modifications that are not synced to AEM server, are irrevocably lost.

## Know the AEM desktop app version {#know-app-version-v2}

Click ![App menu](assets/do-not-localize/more_options_da2.png) to open the app's menu and click **[!UICONTROL Help]** > **[!UICONTROL About]**.

## Issues when upgrading on macOS {#issues-when-upgrading-on-macos}

Occasionally issues may occur when upgrading AEM desktop app on macOS. This is caused by legacy system folder for AEM desktop app preventing new versions of AEM desktop app to load correctly. To remedy this issue, the following folders and files can be manually removed.

Prior to executing the steps below, drag the `Adobe Experience Manager Desktop` application from the macOS Applications folder to the Trash. Then open terminal, and exeucte the following command, providing your password when prompted.

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

## SSL configuration issue {#ssl-config-v2}

The libraries that AEM desktop app uses for HTTP communication utilizes strict SSL enforcement. At times, a connection may succeed using a browser but fails using AEM desktop app. To configure SSL appropriately, install the missing intermediate certificate in Apache. See [How to install an Intermediate CA cert in Apache](https://access.redhat.com/solutions/43575).
