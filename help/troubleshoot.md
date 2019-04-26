---
title: Troubleshoot AEM Desktop App
seo-title: "AEM Assets: Troubleshoot AEM Desktop App"
description: Troubleshoot AEM Desktop App to resolve the occasional issues related to installation, upgrade, configuration, and so on.
seo-description: Troubleshoot AEM Desktop App to resolve the occasional issues related to installation, upgrade, configuration, and so on.
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

# Troubleshoot AEM Desktop App{#troubleshoot-aem-desktop-app}

Troubleshoot AEM Desktop App to resolve the occasional issues related to installation, upgrade, configuration, and so on.

Adobe Experience Manager (AEM) Desktop App includes utilities that assist you in mapping the AEM Assets repository as a network share on desktop (SMB share on Mac OS). Network share is an operating system technology that enables remote sources to be treated as if they were part of a computer's local file system. In the case of Desktop App, a remote AEM instance's digital asset management (DAM) repository structure is targeted as the remote file source.

## Desktop&nbsp;App component overview {#desktop-app-components-v2}

Desktop App includes the following components:

* **The Desktop application**: Mounts/unmounts DAM as a remote file system, and translates file system calls between the locally mounted network share and the remote AEM instance to which it connects.
* **Operating system WebDAV/SMB client**: Handles communication between Windows Explorer/Finder and Desktop App. If a file is retrieved, created, modified, deleted, moved, or copied, the operating system (OS) WebDAV/SMB client communicates this operation to Desktop App. After receiving the communication, Desktop App translates it into native AEM remote API calls. For example, if a user creates a file in the mounted directory, the WebDAV/SMB client initiates a request, which the Desktop App translates into an HTTP request that creates the file in DAM. The WebDAV/SMB client is a built-in component of the OS. It is not affiliated with Desktop App, AEM, or Adobe in any way.
* **Adobe Experience Manager instance**: Provides access to assets stored in the AEM Assets DAM repository. In addition, it performs actions requested by Desktop App on behalf of the local desktop applications interacting with the mounted network share. The target AEM instance should run AEM version 6.1 or higher. AEM instances running previous AEM versions might require extra feature packs and hot fixes installed to become fully functional.

<!--## Intended use cases for AEM Desktop App {#intended-use-cases-for-aem-desktop-app}

AEM Desktop App uses the network share technology to map a remote AEM repository to a local desktop. However, it is not intended as a replacement for a network share holding assets, where users perform digital asset management operations directly from their local desktop. These include moving or copying multiple files, or dragging large folder structures to the AEM Assets network share directly in Finder/Explorer.

AEM Desktop App provides a convenient way of accessing (opening) and editing (saving) DAM assets between the AEM Assets Touch UI and the local desktop. It links assets in the AEM Assets server with your desktop-based workflows.

The following example use case illustrates how AEM Desktop should be used:

* A user logs in to AEM and uses the web UI to locate an asset.
* Using the desktop action capabilities of the AEM web UI, the user either opens, displays, or edits the asset on desktop as necessary.
* AEM Desktop opens the asset in the default editor for the asset's file type.
* The user makes the desired changes to the asset.
* After a file is modified, the user can view the sync status of the file using AEM Desktop's background sync status window.
* Using the context menu of AEM Desktop, the user checks in/out the asset, or returns to the DAM user interface.
* After completing the changes to the file, the user returns to the AEM web UI

This is not the only use case. However, it illustrates how AEM Desktop is a convenient mechanism to access/edit assets locally. You are encouraged to use the DAM web UI as much as possible because it provides a better experience. It provides Adobe more flexibility to meet customer requirements. -->

## Limitations {#limitations-v2}

Review the following limitations.

## Checked-out file limitations {#checked-out-file-limitations}

There are a few known limitations in the way you can interact with checked-out files through Explorer/Finder. If a file is checked out, it should be read-only to anyone except the user that has the file checked out. The implementation of the WebDAV/SMB1 protocol in AEM enforces this rule. However, OS WebDAV/SMB clients often don't interact gracefully with checked-out files. Some oddities are described below.

### General {#general}

When writing to a checked-out file, the lock is only enforced within AEM's WebDAV implementation. Consequently, the lock is only enforced by clients that use WebDAV, such as Desktop App. The lock is not enforced through AEM's web interface. The AEM interface merely displays a lock icon in the card view for assets that are checked out. The icon is cosmetic and has no effect on the behavior of AEM.

### Windows {#windows}

Deleting a file appears to succeed because the file disappears from the file explorer in Windows. However, refreshing the directory and checking in AEM assets shows that the file is still present. In addition, editing files appears to succeed (no warning dialogs or error messages are displayed). However, reopening the file or checking in AEM assets reveals that the file is unchanged.

#### Mac OS X {#mac-os-x}

Replacing a file doesn't display a warning or error, but checking the asset in AEM reveals that it remains unchanged. Refresh or check the asset in AEM to verify that it isn't being modified.

## Clear cache {#clear-cache}

Clearing AEM Desktop's cache is a preliminary troubleshooting task that can resolve several AEM Desktop issues.

You can clear the cache by deleting the application's cache directory at the following locations: Windows: %LocalAppData%\Adobe\AssetsCompanion\Cache\

Mac: ~/Library/Group/Containers/group.com.adobe.aem.desktop/cache/

However, the location can change depending on AEM Desktop's configured AEM endpoint. The value is an encoded version of the targeted URL. For example, if the application is targeting `http://localhost:4502`, the directory name is `http%3A%2F%2Flocalhost%3A4502%2F`.

To clear the cache, delete the &lt;Encoded AEM Endpoint&gt; directory.

>[!NOTE]
>
>If you clear AEM Desktop cache, local file changes that are not synced to AEM are lost.

## Know the AEM desktop app version {#know-app-version}

The procedure to ascertain the AEM Desktop version is the same for both Windows and Mac OS.

Click the AEM Desktop icon, and then choose **About**. The version number is displayed on the screen.

## Upgrading AEM Desktop App on macOS {#upgrading-aem-desktop-app-on-macos}

Occasionally issues may occur when upgrading AEM Desktop App on macOS. This is caused by legacy system folder for AEM Desktop App preventing new versions of AEM Desktop to load correctly. To remedy this issue, the following folders and files can be manually removed.

Prior to executing the steps below, drag the "Adobe Experience Manager Desktop" application from the macOS Applications folder to the Trash. Then open terminal, and exeucte the following command, providing your password when prompted.

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

## Move files across folders {#move-files-across-folders}

How do we want to document this use case?

### SSL configuration issue {#ssl-config}

The libraries that AEM Desktop App uses for HTTP communication utilizes strict SSL enforcement. At times, a connection may succeed using a browser but fails using AEM Desktop App. To configure SSL appropriately, install the missing intermediate certificate in Apache. See [How to install an Intermediate CA cert in Apache](https://access.redhat.com/solutions/43575).

## Check log files {#check-log-files}

Depending upon your operating system, you can find the log files for AEM Desktop at the following locations:

* Windows: `%LocalAppData%\Adobe\AssetsCompanion\Logs`
* Mac: `~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`