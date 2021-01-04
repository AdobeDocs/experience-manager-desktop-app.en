---
title: Troubleshoot [!DNL Adobe Experience Manager] desktop app version 1.x
description: Troubleshoot [!DNL Adobe Experience Manager] desktop app version 1.x to resolve the occasional issues related to installation, upgrade, and configuration.
---

# Troubleshoot [!DNL Adobe Experience Manager] desktop app v1.x {#troubleshoot-aem-desktop-app}

Troubleshoot AEM desktop app to resolve the occasional issues related to installation, upgrade, configuration, and so on.

[!DNL Adobe Experience Manager] desktop app includes utilities that assist you in mapping the AEM Assets repository as a network share on desktop (SMB share on Mac OS). Network share is an operating system technology that enables remote sources to be treated as if they were part of a computer's local file system. In the case of desktop app, a remote AEM instance's digital asset management (DAM) repository structure is targeted as the remote file source. The following diagram describes the desktop app topology:

![desktop app diagram](assets/aem-desktopapp-architecture.png)

With this architecture, desktop app intercepts file system calls (open, close, read, write, and so on) to the mounted network share, and translates them into native AEM HTTP calls to the AEM server. Files are cached locally. For more details, see [Use AEM desktop app v1.x](use-app-v1.md).

## AEM desktop app component overview {#desktop-app-component-overview}

desktop app includes the following components:

* **The desktop application**: The application mounts or unmounts DAM as a remote file system, and translates file system calls between the locally mounted network share and the remote AEM instance to which it connects.
* **Operating system WebDAV/SMB client**: Handles communication between Windows Explorer/Finder and desktop app. If a file is retrieved, created, modified, deleted, moved, or copied, the operating system (OS) WebDAV/SMB client communicates this operation to desktop app. After receiving the communication, desktop app translates it into native AEM remote API calls. For example, if a user creates a file in the mounted directory, the WebDAV/SMB client initiates a request, which the desktop app translates into an HTTP request that creates the file in DAM. The WebDAV/SMB client is a built-in component of the OS. It is not affiliated with desktop app, AEM, or Adobe in any way.
* **Adobe Experience Manager instance**: Provides access to assets stored in the AEM Assets DAM repository. In addition, it performs actions requested by desktop app on behalf of the local desktop applications interacting with the mounted network share. The target AEM instance should run AEM version 6.1 or higher. AEM instances running previous AEM versions might require extra feature packs and hot fixes installed to become fully functional.

## Intended use cases for AEM desktop app {#intended-use-cases-for-aem-desktop-app}

AEM desktop app uses the network share technology to map a remote AEM repository to a local desktop. However, it is not intended as a replacement for a network share holding assets, where users perform digital asset management operations directly from their local desktop. These include moving or copying multiple files, or dragging large folder structures to the AEM Assets network share directly in Finder/Explorer.

AEM desktop app provides a convenient way of accessing (opening) and editing (saving) DAM assets between the AEM Assets Touch UI and the local desktop. It links assets in the AEM Assets server with your desktop-based workflows.

The following example use case illustrates how AEM Desktop should be used:

* A user logs in to AEM and uses the web UI to locate an asset.
* Using the desktop action capabilities of the AEM web UI, the user either opens, displays, or edits the asset on desktop as necessary.
* AEM Desktop opens the asset in the default editor for the asset's file type.
* The user makes the desired changes to the asset.
* After a file is modified, the user can view the sync status of the file using AEM Desktop's background sync status window.
* Using the context menu of AEM Desktop, the user checks in/out the asset, or returns to the DAM user interface.
* After completing the changes to the file, the user returns to the AEM web UI

This is not the only use case. However, it illustrates how AEM Desktop is a convenient mechanism to access/edit assets locally. You are encouraged to use the DAM web UI as much as possible because it provides a better experience. It provides Adobe more flexibility to meet customer requirements.

## Limitations {#limitations}

WebDAV/SMB1 network share provides the convenience of working with files in an Explorer/Finder window. However, Explorer/Finder and AEM communicate over a network connection that has certain limitations. For example, the time consumed to copy a 1-GB file to the mounted WebDAV/SMB directory is approximately the same as the time required to upload a 1-GB file to a website using a web browser. In fact, in the former case, the duration may be longer due to inefficiencies of the WebDAV/SMB protocol and the OS's WebDAV/SMB clients (particularly Mac OS X).

There are limitations to the types of tasks that can be performed from a mounted directory. In general, working with large files especially over a poor/high latency/low bandwidth network connection might be challenging, especially when editing large files.

Adobe recommends that you perform some use-case testing before committing to a client that certain types of files can be efficiently edited in-place from the mounted directory.

AEM Desktop is not suitable for performing intensive file system manipulation, including but not limited to:

* Moving or copying files and directories
* Adding many assets to AEM
* Searching for and opening files through the file system, except for browsing folders
* Compressing or decompressing file archives

Due to limitations in the operating system, Windows has a file size limitation of 4,294,967,295 bytes (approximately 4.29 GB). It is due to a registry setting that defines how large a file on a network share can be. The value of the registry setting is a DWORD with a maximum size that equals the referenced number.

[!DNL Experience Manager] desktop app does not have a configurable timeout value that disconnects the connection between [!DNL Experience Manager] server and desktop app after a fixed time interval. When uploading large assets, if the connection gets timeout after a while, the app retries to upload the asset a few times by increasing the upload timeout. There is no recommended way to change the default timeout settings.

## Caching and communication with AEM {#caching-and-communication-with-aem}

AEM desktop app provides internal caching and background upload capabilities to improve end user experience. When you save a large file, it is first saved locally to let you continue working. After sometime (currently 30 seconds), the file is then sent to the AEM server in the background.

Unlike Creative Cloud Desktop or other file sync solutions, such Microsoft One Drive, AEM desktop app is not a full Desktop Sync client. The reason for this is that it provides access to the entire AEM Assets repository, which can be extremely large (hundreds of gigabytes or terabytes) for a full synchronization.

Caching provides the ability to limit the network/storage overhead to only a subset of assets that are relevant to the user.

>[!CAUTION]
>
>Adobe recommends turning off thumbnail generation to make browsing faster. If you enable icon previews, the app caches the digital assets when you navigate through the mounted folder. The app also downloads assets that the user may not care about, which adds load to the server, consumes the user's bandwidth, and uses more of the user's disk space.

Here is how AEM desktop app performs caching:

* When you open a folder in Finder and thumbnails/previews of files are displayed, or when you open a file in an application, desktop app caches the file binary.
* When you store files via Finder or other desktop applications, the file is stored locally first (cached) and the operating system is notified. The file is then queued for upload to server in the background, and eventually uploaded over network. In case of a network error, desktop app retries uploading of the whole file for a maximum of three times. If the fails to upload after three retries, the file is marked as a conflicting file, and the status is displayed via the Background Upload Queue Status window. desktop app does not attempt to update the file any more. The user should update the file and re-upload it after the connectivity is restored

Every operation is not cached locally. The following are transmitted to the AEM Server immediately without local caching:

* Any operations on folders, for example create, delete, and so on
* The Folder Upload feature introduced in version 1.4 uploads a local folder hierarchy without caching the files locally

## Individual operations {#individual-operations}

When troubleshooting sub-optimized performance for individual users, first review [Limitations](https://helpx.adobe.com/experience-manager/desktop-app/troubleshooting-desktop-app.html#limitations). The subsequent sections include suggestions to improve performance for individual users.

## Bandwidth recommendations {#bandwidth-recommendations}

The bandwidth available to an individual user plays a critical role in the performance of the WebDAV/SMB client.

Adobe recommends that an individual user's upload speed to be close to 10 Mbps. For wireless connections, bandwidth is often shared between multiple users. If multiple users simultaneously perform tasks that consume network bandwidth, the performance can degrade even further. To avoid such issues, use a wired connection.

## Windows-specific configurations {#windows-specific-configurations}

If you run AEM on Windows, you can configure Windows to enhance the performance of the WebDAV client. For more information, go to [https://support.microsoft.com/en-us/kb/2445570](https://support.microsoft.com/en-us/kb/2445570).

On Windows 7, modifying IE settings can improve the performance of WebDAV. For details, see how to [fix slow WebDAV performance in Windows 7](https://oddballupdate.com/2009/12/fix-slow-webdav-performance-in-windows-7/).

## Concurrent operations {#concurrent-operations}

When you interact with a file locally, AEM Desktop checks whether a newer version of the file is available in AEM. If a new version is available, the application downloads a fresh copy of the file to the local cache. However, AEM Desktop does not overwrite a locally cached file if it has been modified. This feature prevents your work from being overwritten inadvertently.

When the same file is modified both locally and in AEM, the locally modified version overwrites the version in AEM. In this case, the previous version is available in the asset's timeline. You can verify both versions and resolve any conflicts.

If a local file is inconsistent with the version available in the server, the background upload status dialog notifies you about the conflict. To resolve the issue, open the conflicting file and save it. Saving the file forces AEM Desktop to sync your latest local changes to AEM. You can view previous versions of the asset in the timeline and resolve any conflicts.

You should take into account additional factors when multiple users attempt to work in separate mounted directories targeting the same AEM instance. In particular, the following factors are important:

* The amount of bandwidth available on the users' originating network
* Network configuration, such as firewalls or proxies, of the originating network
* Amount of bandwidth available in the target AEM instance's network
* Whether a dispatcher is present before the target AEM instance
* Current load on the target AEM instance

## Additional AEM configurations {#additional-aem-configurations}

If the WebDAV/SMB performance degrades drastically when multiple users work simultaneously, you can configure a few things in AEM, which can help improve performance.

## Update Asset transient workflows {#update-asset-transient-workflows}

You can improve the performance at the AEM side by enabling transient workflows for the DAM Update Asset workflow. Enabling transient workflows reduces the processing power required to update assets when they are created or modified in AEM.

1. Navigate to `/miscadmin` in the AEM instance to be configured (for example, `http://[Server]:[Port]/miscadmin`).
1. From the navigation tree, expand **Tools** &gt; **Workflow** &gt; **Models** &gt; **dam**.
1. Double-click **DAM Update Asset**.
1. From the floating tools panel, switch to the **Page** tab and then click **Page Properties**.
1. Select the **Transient Workflow** check box, and click **OK**.

### Adjust Granite Transient Workflow queue {#adjust-granite-transient-workflow-queue}

Another method for improving AEM performance is to configure the value of the maximum parallel jobs for the Granite Transient Workflow Queue job. The recommended value is roughly half the number of the CPU available with the server. To adjust the value, perform these steps:

1. Navigate to */system/console/configMgr* in the AEM instance to be configured (for example, `http://[aem_server]:[port]/system/console/configMgr`).
1. Search for **QueueConfiguration**, and click to open each job until you locate the **Granite Transient Workflow Queue** job. Click the Edit  beside it.
1. Change the **Maximum Parallel Jobs** value, and click **Save**.

## AWS configuration {#aws-configuration}

Owing to network bandwidth limitations, the performance of WebDAV/SMB may degrade when multiple users work simultaneously. Adobe recommends increasing the size of the AWS instance for a target AEM instance that runs on AWS to enhance the performance of WebDAV/SMB.

This measure specifically boosts the amount of network bandwidth available to the server. Here are some details:

* The amount of network bandwidth dedicated to an AWS instance increases as the size of the instance increases. For information about how much bandwidth is available for each instance size, see [AWS documentation](https://aws.amazon.com/ec2/instance-types/).
* When troubleshooting for a large client, Adobe configured the size of its AEM instance to c4.8xlarge, primarily for the 4000 Mbps of dedicated bandwidth that it provides.
* If there is a dispatcher ahead of the AEM instance, ensure that it is of appropriate size. If the AEM instance provides 4000 Mbps but the dispatcher only provides 500 Mbps, the effective bandwidth is only 500 Mbps. It is because the dispatcher creates a network bottleneck.

## Checked-out file limitations {#checked-out-file-limitations}

There are a few known limitations in the way you can interact with checked-out files through Explorer/Finder. If a file is checked out, it should be read-only to anyone except the user that has the file checked out. The implementation of the WebDAV/SMB1 protocol in AEM enforces this rule. However, OS WebDAV/SMB clients often don't interact gracefully with checked-out files. Some oddities are described below.

### General {#general}

When writing to a checked-out file, the lock is only enforced within AEM WebDAV implementation. Consequently, the lock is only enforced by clients that use WebDAV, such as desktop app. The lock is not enforced through AEM web interface. The AEM interface merely displays a lock icon in the card view for assets that are checked out. The icon is cosmetic and has no effect on the behavior of AEM.

In general, the WebDAV clients don't always behave as expected. There may be additional issues. However, refreshing or checking the asset in AEM is a sound way to verify that an asset isn't being modified. This behavior is typical of the OS WebDAV clients, which isn't under Adobe's control.

### Windows {#windows}

Deleting a file appears to succeed because the file disappears from the file explorer in Windows. However, refreshing the directory and checking in AEM assets shows that the file is still present. In addition, editing files appears to succeed (no warning dialogs or error messages are displayed). However, reopening the file or checking in AEM assets reveals that the file is unchanged.

#### Mac OS X {#mac-os-x}

Replacing a file doesn't display a warning or error, but checking the asset in AEM reveals that it remains unchanged. Refresh or check the asset in AEM to verify that it isn't being modified.

## Troubleshooting desktop app icon issues (Mac OS X) {#troubleshooting-desktop-app-icon-issues-mac-os-x}

After you install desktop app, the desktop app menu icon appears in the menu bar. If the icon doesn't appear, perform these steps to resolve the issue:

1. Open the operating system terminal window.
1. Type the following command at the command prompt, and then press Enter:

   ```shell
    cd ../Library/Caches.
   ```

1. Type the following command, and press Enter:

   ```shell
   rm -r com.adobe.aem.assetscompanion
   ```

1. Type the following command, and press Enter:

   ```shell
   cd ~/Library/Preferences
   ```

1. Type the following command, and press Enter:

   ```shell
   rm com.adobe.aem.assetscompanion.plist
   ```

1. Type the following command, and press Enter:

   ```shell
   rm ~/Library/Group\ Containers/group.com.adobe.aem.desktop/*
   ```

1. Restart the system.

AEM Desktop attempts to sync any given file three times. If the file fails to sync after the third attempt, AEM Desktop considers the file to be in conflict and notifies you via the background upload status window. A conflict state indicates that your latest changes are still available to you locally, but they are not synced back to AEM. AEM desktop app no longer attempts to sync.

The simplest way to fix this situation is to open the conflicting file and save it again. It forces AEM Desktop to attempt synchronization for an additional three occasions. If the file still fails to sync, see the sections below for more help.

## Clearing AEM Desktop cache {#clearing-aem-desktop-cache}

Clearing AEM Desktop's cache is a preliminary troubleshooting task that can resolve several AEM Desktop issues.

You can clear the cache by deleting the application's cache directory at the following locations.
In Windows, `%LocalAppData%\Adobe\AssetsCompanion\Cache\`

In Mac, `~/Library/Group/Containers/group.com.adobe.aem.desktop/cache/`

However, the location can change depending on AEM Desktop's configured AEM endpoint. The value is an encoded version of the targeted URL. For example, if the application is targeting `http://localhost:4502`, the directory name is `http%3A%2F%2Flocalhost%3A4502%2F`.

To clear the cache, delete the &lt;Encoded AEM Endpoint&gt; directory.

>[!NOTE]
>
>If you clear AEM Desktop cache, local file changes that are not synced to AEM are lost.

>[!NOTE]
>
>Starting with AEM desktop app version 1.5, there is an option in the desktop app UI to clear the cache.

## Finding the AEM Desktop version {#finding-the-aem-desktop-version}

The procedure to ascertain the AEM Desktop version is the same for both Windows and Mac OS.

Click the AEM Desktop icon, and then choose **About**. The version number is displayed on the screen.

## Upgrading AEM desktop app on macOS {#upgrading-aem-desktop-app-on-macos}

Occasionally issues may occur when upgrading AEM desktop app on macOS. This is caused by legacy system folder for AEM desktop app preventing new versions of AEM Desktop to load correctly. To remedy this issue, the following folders and files can be manually removed.

Prior to executing the steps below, drag the "Adobe Experience Manager Desktop" application from the macOS Applications folder to the Trash. Then open terminal, and execute the following command, providing your password when prompted.

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

## Saving a file checked out by others {#saving-a-file-checked-out-by-others}

Technical limitations of the operating system prevent users from having a consistent experience when attempting to overwrite a file that is checked out by others. The experience varies depending on the application used to edit the checked out file. Sometimes, the application displays an error message indicating a disk write failure or displays a seemingly unrelated or generic error. On other occasions, no error message is displayed and the operation appears to succeed.

In this case, closing and reopening the file may reveal that the contents are unchanged. However, some applications may store a backup of the file so your changes can be applied.

Regardless of the behavior, the file remains unchanged when you check it in. Even if a different version of the file is displayed, the changes are not synced to AEM.

## Troubleshooting problems around moving files {#troubleshooting-problems-around-moving-files}

The server API requires additional headers, X-Destination, X-Depth, and X-Overwrite, to be passed for the move and copy operations to work. The dispatcher does not pass these headers by default, which causes these operations to fail. For more information, see [Connecting to AEM Behind a Dispatcher](install-configure-app-v1.md#connect-to-an-aem-instance-behind-a-dispatcher).

## Troubleshooting AEM Desktop connection issues {#troubleshooting-aem-desktop-connection-issues}

### SAML redirect issue {#saml-redirect-issue}

The most common reason for issues with AEM Desktop connecting to your SSO-enabled (SAML) AEM instance is that the SAML process does not redirect back to the originally requested path. Alternatively, the connection may be redirected to a host that not configured in AEM desktop. Perform these steps to verify the login process:

1. Open a web browser.
1. In the address bar, specify the URL `/content/dam.json`.
1. Replace the URL with the target AEM instance, for example `http://localhost:4502/content/dam.json`.
1. Log on to AEM.
1. After logging in, check the browser's current address in the address bar. It should match the URL that you initially entered.
1. Verify that everything before `/content/dam.json` matches the target AEM value configured in AEM Desktop.

### SSL configuration issue {#ssl-configuration-issue}

The libraries that AEM desktop app uses for HTTP communication utilizes strict SSL enforcement. At times, a connection may succeed using a browser but fails using AEM desktop app. To configure SSL appropriately, install the missing intermediate certificate in Apache. See [How to install an Intermediate CA cert in Apache](https://access.redhat.com/solutions/43575).

## Using AEM Desktop with dispatcher {#using-aem-desktop-with-dispatcher}

AEM Desktop works with AEM deployments behind a dispatcher, which is a default and recommended configuration for AEM servers. AEM dispatchers in front of AEM authoring environments are typically configured to skip caching DAM assets. Therefore, dispatchers do not provide additional caching from the AEM Desktop standpoint. Ensure that the dispatcher configuration is adjusted to work for AEM Desktop. For additional details, see [Connecting to AEM behind a dispatcher](install-configure-app-v1.md#connect-to-an-aem-instance-behind-a-dispatcher).

## Checking for log files {#checking-for-log-files}

Depending upon your operating system, you can find the log files for AEM Desktop at the following locations:

* Windows: `%LocalAppData%\Adobe\AssetsCompanion\Logs`
* Mac: `~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`
