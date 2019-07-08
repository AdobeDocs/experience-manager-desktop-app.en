---
title: Troubleshoot AEM desktop app
seo-title: "AEM Assets: Troubleshoot AEM desktop app"
description: Troubleshoot AEM desktop app to resolve the occasional issues related to installation, upgrade, configuration, and so on.
seo-description: Troubleshoot AEM desktop app to resolve the occasional issues related to installation, upgrade, configuration, and so on.
uuid: ce98a3e7-5454-41be-aaaa-4252b3e0f8dd
contentOwner: asgupta
content-strategy: redirect-pointer
content-type: troubleshooting
products: SG_EXPERIENCEMANAGER
discoiquuid: f5eb222a-6cdf-4ae3-9cf2-755c873f397c
index: y
internal: n
snippet: y
---

# Troubleshoot AEM desktop app {#troubleshoot-v2}

Adobe Experience Manager (AEM) desktop app connects to a remote AEM deployment's Digital Asset Management (DAM) repository. The app fetches repository information and search results on your machine, downloads and uploads files and folders, and includes capabilities to manage conflicts with AEM Assets UI.

## Best practices {#best-practices-to-prevent-troubles}

Adhering to the following best practices will help you prevent some of the issues and their troubleshooting.

* **Understand how the desktop app works**: Before starting to use the application, spend a few minutes knowing how the app works. Know about linking between Web UI and desktop, repository mapping, asset caching, saving locally and uploading in background. See [how it works](release-notes.md/#how-app-works).

* **Best practices to avoid conflicts**: To avoid potential conflicts when collaborating on multiple assets, see [avoid editing conflicts](using.md#adv-workflow-collaborate-avoid-conflicts).

* **Use folder upload for large, hierarchical folders**: Instead of using the Assets web interface or other methods, use AEM desktop app to upload large folders. The app uploads the assets in background with logging and monitoring. See [bulk upload assets](using.md#bulk-upload-assets).

* **Use the latest version**: Use the latest app version and always check for compatbility before installing either a new app version or before upgrading to a newer AEM version. See [release notes](release-notes.md).

* **Mind the network**: Network performance is critical to AEM desktop app's performance. If you face slowed response to file transfers or bulk operations, turn off the features or apps that might cause lots of network traffic (like thumbnails in Finder) for the mapped network share.

* **Unsupported use cases for desktop app**: Do not use the app in the following ways:
    * Asset migration: Needs planning and other tools.
    * Replacement for network file share: Heavy-duty DAM operations like moving large folders, large uploads, finding files are better done from the Web UI.
    * The app is not a sync client: Design principles and usage patterns are different than in-sync clients like Microsoft OneDrive or Adobe Creative Cloud desktop sync.

## Desktop App component overview {#desktop-app-components-v2}

Desktop app includes the following components:

* **The Desktop application**: Mounts/unmounts DAM as a remote file system, and translates file system calls between the locally mounted network share and the remote AEM instance to which it connects.
* **Operating system WebDAV/SMB client**: Handles communication between Windows Explorer/Finder and desktop app. If a file is retrieved, created, modified, deleted, moved, or copied, the operating system (OS) WebDAV/SMB client communicates this operation to desktop app. After receiving the communication, desktop app translates it into native AEM remote API calls. For example, if a user creates a file in the mounted directory, the WebDAV/SMB client initiates a request, which the desktop app translates into an HTTP request that creates the file in DAM. The WebDAV/SMB client is a built-in component of the OS. It is not affiliated with desktop app, AEM, or Adobe in any way.
* **Adobe Experience Manager instance**: Provides access to assets stored in the AEM Assets DAM repository. In addition, it performs actions requested by desktop app on behalf of the local desktop applications interacting with the mounted network share. The target AEM instance should run a supported AEM version. AEM instances may require extra feature packs and hot fixes installed to become fully functional and secure.

## Limitations {#limitations-v2}

Review the following limitations.

### Checked-out file limitations {#checked-out-file-limitations-v2}

There are a few known limitations in the way you can interact with checked-out files through Explorer/Finder. If a file is checked out, it should be read-only to anyone except the user that has the file checked out. The implementation of the WebDAV/SMB1 protocol in AEM enforces this rule. However, OS WebDAV/SMB clients often don't interact gracefully with checked-out files. Some oddities are described below.

### General {#general-v2}

When writing to a checked-out file, the lock is only enforced within AEM's WebDAV implementation. Consequently, the lock is only enforced by clients that use WebDAV, such as desktop app. The lock is not enforced through AEM's web interface. The AEM interface merely displays a lock icon in the card view for assets that are checked out. The icon is cosmetic and has no effect on the behavior of AEM.

### Windows {#windows-v2}

Deleting a file appears to succeed because the file disappears from the file explorer in Windows. However, refreshing the directory and checking in AEM assets shows that the file is still present. In addition, editing files appears to succeed (no warning dialogs or error messages are displayed). However, reopening the file or checking in AEM assets reveals that the file is unchanged.

### Mac OS X {#mac-os-x-v2}

Replacing a file doesn't display a warning or error, but checking the asset in AEM reveals that it remains unchanged. Refresh or check the asset in AEM to verify that it isn't being modified.

## Clear cache {#clear-cache-v2}

Clearing AEM Desktop's cache is a preliminary troubleshooting task that can resolve several AEM Desktop issues.

You can clear the cache by deleting the application's cache directory at the following locations: Windows: %LocalAppData%\Adobe\AssetsCompanion\Cache\

Mac: ~/Library/Group/Containers/group.com.adobe.aem.desktop/cache/

However, the location can change depending on AEM Desktop's configured AEM endpoint. The value is an encoded version of the targeted URL. For example, if the application is targeting `http://localhost:4502`, the directory name is `http%3A%2F%2Flocalhost%3A4502%2F`.

To clear the cache, delete the &lt;Encoded AEM Endpoint&gt; directory.

>[!NOTE]
>
>If you clear AEM Desktop cache, local file changes that are not synced to AEM are lost.

## Know the AEM desktop app version {#know-app-version-v2}

The procedure to ascertain the AEM Desktop version is the same for both Windows and Mac OS.

Click the AEM Desktop icon, and then choose **About**. The version number is displayed on the screen.

## Upgrade AEM desktop app on macOS {#upgrade-aem-desktop-app-on-macos-v2}

Occasionally issues may occur when upgrading AEM desktop app on macOS. This is caused by legacy system folder for AEM desktop app preventing new versions of AEM Desktop to load correctly. To remedy this issue, the following folders and files can be manually removed.

Prior to executing the steps below, drag the "Adobe Experience Manager Desktop" application from the macOS Applications folder to the Trash. Then open terminal, and exeucte the following command, providing your password when prompted.

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

## Save a file checked out by others {#save-a-file-checked-out-by-others-v2}

Technical limitations of the operating system prevent users from having a consistent experience when attempting to overwrite a file that is checked out by others. The experience varies depending on the application used to edit the checked out file. Sometimes, the application displays an error message indicating a disk write failure or displays a seemingly unrelated or generic error. On other occasions, no error message is displayed and the operation appears to succeed.

In this case, closing and reopening the file may reveal that the contents are unchanged. However, some applications may store a backup of the file so your changes can be applied.

Regardless of the behavior, the file remains unchanged when you check it in. Even if a different version of the file is displayed, the changes are not synced to AEM.

## SSL configuration issue {#ssl-config-v2}

The libraries that AEM desktop app uses for HTTP communication utilizes strict SSL enforcement. At times, a connection may succeed using a browser but fails using AEM desktop app. To configure SSL appropriately, install the missing intermediate certificate in Apache. See [How to install an Intermediate CA cert in Apache](https://access.redhat.com/solutions/43575).

## Check log files {#check-log-files-v2}

Depending upon your operating system, you can find the log files for AEM desktop app at the following locations:

* **Windows**: `%LocalAppData%\Adobe\AssetsCompanion\Logs`
* **Mac**: `~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`

When uploading many assets, if some files fail to upload, see the following logs to identify the failed uploads in `backend.log` file at the above location.
