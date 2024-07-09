---
title: Release notes of desktop app v1.10
description: Release details, enhancements, new features, compatibility, and download links for AEM desktop app version 1.10.
exl-id: 886864e0-016a-4a17-b3ba-4b18a514214a
---
# [!DNL Adobe Experience Manager] desktop app v1.10 release notes {#aem-desktop-app-release-notes}

For desktop app v1.x release, the following are the download links and AEM compatibility information.

| Products | [!DNL Adobe Experience Manager] desktop app |
|--- |--- |
| Version | 1.10 (1.10.0.6 on Mac and 1.10.0.3 on Windows) |
| Type | Minor release |
| Date | 1.10.0.6 (Mac): April 15, 2020; 1.10.0.3 (Win): August 31, 2018 |
| Download URLs | [macOS X 64 bit](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-osx-1.10.0.6.dmg); [Windows 32 bit](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-win32-1.10.0.3.exe); [Windows 64 bit](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-win64-1.10.0.3.exe) |
| Compatibility | AEM 6.5.x; AEM 6.4.x; AEM 6.3 SP2; AEM 6.2 SP1 CFP2+; AEM 6.1 SP2 CFP7+ |

>[!NOTE]
>
>Cache size limit is not enforced. When the desktop app starts, the cache size is calculated once, and a notification is shown if the size is close to the predefined limit.

## System requirements and prerequisites {#system-requirements-and-prerequisites}

[!DNL Adobe Experience Manager] desktop app is compatible with the following operating systems:

* macOS X 10.10 or newer, with latest bug fixes.

* Windows 10 with the latest service packs and bug fixes.

Adobe recommends using the latest version of the AEM desktop app to ensure you are using the latest functionality, the most recent bug fixes, and the best possible performance.

The version of AEM desktop app you are planning to install on your local machine requires a specific AEM server 
version / additional server-side components (service packs, hot fixes or feature packs). Ensure that the AEM server is properly configured before you connect to it for the first time. If you require help, contact your AEM administrator.

See the [detailed compatibility matrix](#compatibilitymatrix) at the end of this document to evaluate the prerequisites for your setup.

## What is new in desktop app v1.10 {#what-s-new-in-aem-desktop-app}

AEM desktop app 1.10 focuses on improving user experience around large uploads, information about the background operations, and optimized experience when opening assets with linked files (like InDesign).

>[!NOTE]
>
>If you are using macOS 10.15.4 or newer, use at least version 1.10.0.6 of the app. This patch release complies with [Apple notarization requirements](https://developer.apple.com/news/?id=04102019a).

**Local Editing / Check-Out**: Automatic uploads of changes saved to assets can be disabled in the status window. That way the user can continue working on files and saving changes and then, when they are ready, decide to upload all changes.

**Simplified Asset Status Window**. The status window was simplified. The [!UICONTROL Uploads] tab now shows both individual assets, and folder or bulk uploads. The previous bulk uploads tab was removed.

**Application Icon to Indicate Bulk Uploads**. The application icon indicates that a bulk upload is in progress by showing a "transfer" overlay.

**Notifications for Update Conflicts**. When the application detects a conflict during an asset update, it displays a notification, allowing the user to review it without monitoring the status window. At startup, the application checks for all conflicts, enabling the user to resolve them.

**Better Handling of Connection Losses**. Bulk uploads are paused if there is a connection loss, and the user can resume later. A [!UICONTROL Retry] option is available to retry a failed upload of an individual file.

## Installation instructions {#installation-instructions}

For detailed instructions, see [Install and configure the AEM desktop app](install-configure-app-v1.md).

## Enhancements in the previous versions {#enhancements-in-the-previous-versions}

This release extends and replaces the previous versions of the [!DNL Experience Manager] desktop app, which provided the following key enhancements:

* **Version 1.9 / 1.9.1**: resumable uploads, improved status window, application icons indicating status of application / connection, pre-fetching of linked assets for InDesign files.

* **Version 1.8**: better control of cache size for the user, improved login experience for SAML / SSO on Windows, supporting `.pac` network proxy on Mac, and customer-reported issues.

* **Version 1.7**: improvements in stability and caching logic, better support for network proxy, and ability to clean up internal files after uninstallation.

* **Version 1.6**: improvements in the login process for various AEM security configurations and application stability and performance.

* **Version 1.5**: application stability and resilience against various networking problems, better supportability.

* **Version 1.4**: the ability to upload hierarchical folders in the background with the progress monitoring.

* **Version 1.3**: performance enhancements and stability of accessing files and saving changes to AEM, especially from Creative Cloud desktop applications, such as InDesign, Illustrator, or Photoshop. It aimed to provide users with a more local desktop-like experience when working with files, while simultaneously handling network data transfer operations in the background.

### Enhancements available since AEM desktop app 1.9 {#Enhancements-Available-Since-AEM-Desktop-App-19x}

[!DNL Adobe Experience Manager] desktop app version 1.9.1 was a patch release. It was designed to address key customer issues with asset checkout. And, address copying files from a network share to a local directory.

* Assets checked out by one users should not be available for modification for other users (CQ-4246009)

* Support copy from a mapped folder to a local folder when the user folder is on a separate disk partition (CQ-4243978)

AEM desktop app 1.9 focused on improving user experience around large uploads, information about the background operations, and optimized experience when opening assets with linked files (like InDesign).

**Resumable Uploads**
For uploads, especially around large files, there is an option to pause / resume them in the new Asset Status window.

**Improved Asset Status Window**
An improved Asset Status window provides the following information about assets.

[!UICONTROL Changes]

* Displays currently queued changes.

* Displays in-progress uploads with a progress bar, transfer rate, total file size, and the amount transferred so far.

* Completed uploads shown with total transferred and final rate.

* Failed uploads display along with an error message and transfer information, if available.

* Uploads that have failed three times show an error message.

* Conflicting files are shown with an icon that the user can click. Clicking the icon shows a dialog with an explanation and two options:

  * [!UICONTROL Keep Mine] immediately uploads the file to the server.

  * [!UICONTROL Overwrite Mine] immediately deletes the local file and downloads a new copy from the server.

[!UICONTROL Downloads]

* Displays in-progress downloads, including a transfer rate and size transferred so far.

* Completed downloads are shown with total transferred, final rate, and an icon that opens the file when clicked (only available for single files).

* Failed downloads displayed with an error message and transfer information, if available.

* The footer shows the total number of files downloaded and the average transfer rate.

* If a user chooses to open or edit multiple files from the [!DNL Experience Manager Assets] Web interface, they are grouped together. For example, myasset.jpeg and 4 more files.

* When downloading InDesign documents with linked assets from AEM Assets, the desktop app first downloads all linked assets before opening the document and indicating the download status. For example, 5 of 24.

[!UICONTROL Bulk Uploads]

Uploading large folder hierarchies via [!UICONTROL Create] > [!UICONTROL Upload Folder] in the AEM Web UI triggers this dialog box. The same occurs when copying and selecting "Paste Assets" in Finder or Explorer in the desktop app context menu.

* Displays in-progress uploads, including a progress bar and the name of the file currently being transferred.

* In-progress uploads include an icon that cancels the upload when clicked. The transfer stops after the currently transferring file completes.

* Failed transfer processes are displayed with an error message (only if the entire transfer fails).

* If an individual file fails to transfer, it shows up on the tab as an error. Otherwise, individual files do not show on the tab * only a single entry for the entire upload.

**Icons to Indicate Status of Background Operations**

The application icon indicates the state of background operations to provide a better visual cue to the users. For example, when the application is not connected to AEM, the icon is grayed out. When there is an active upload it shows a "sync" overlay, and so on.

**Pre-fetching of Linked Assets**

To enhance the user experience with InDesign documents containing linked assets stored in AEM, the desktop app pre-fetches these linked files to the local cache. This flow occurs before it downloads and opens the InDesign document. That way the user has the linked files available locally, and does not need to wait longer when accessing assets in InDesign (in the Links panel).
Pre-fetching only works if AEM recognizes the links on the server side. An asset with recognized links has a list of "References" listed in the Properties view of the InDesign asset.

### Enhancements Available Since AEM desktop app 1.8.x {#enhancements-available-since-aem-desktop-app-18x}

AEM desktop app 1.8.1 fast-follow release added improvements when opening multiple files at once from AEM UI to the 1.8 release (CQ-4237747, CQ-4238780). Enhancements in AEM desktop app 1.8 are:

* Caching: new UI for managing AEM desktop app cache (CQ-4208690), including,

  * view current cache size

  * define the maximum cache size before a notification is sent

  * Cache size is checked on desktop app start only, and a notification is shown if it is reaching the configured limit

  * clearing cache button is now available in the new UI

* Log in: (Win) Fixed login to AEM instance configured to use SAML and SSL (CQ-4216353)

* Network:

  * when an AEM session expires, the user is now notified and can click on the notification to log in again (CQ-4202028).

  * (Mac) Add support for connecting to AEM by way of using the `.pac` proxy configuration (CQ-4233430).

  * (Win) fix issues with Advanced - Login URL dialog (CQ-4236061).

* Bug fixes:

  * More Asset Info dialog box: sometimes the action bar was not visible (CQ-4208540).

  * (Win) File can now be synchronized after reverting to a previous version from AEM Assets UI (CQ-4216411).

### Enhancements Available Since AEM desktop app 1.7 {#Enhancements-Available-Since-AEM-Desktop-App-17}

* Stability:

  * Improved stability when the AEM desktop app connects to an overloaded AEM server (CQ-4224803).

  * Improved stability when many files are requested (CQ-4224212).

  * Improved asset update with additional check (CQ-4228291).

* Caching:

  * Fix disk errors and opening problems when opening files in Photoshop, InDesign, Finder (CQ-4223993, CQ-4217603, CQ-4223717).

  * Improved caching to avoid zero-size binaries (CQ-4216599).

* Login: Allow for connecting with strictSSL disabled for special configurations (like locally issued certificates) (CQ-4223949).

* Networking: Improved support for connecting over network proxy (CQ-4223477, CQ-4221280, CQ-4206854).

* Installation and uninstallation:

  * (Win) Cleaner uninstallation (CQ-4220906).

  * [Windows 32bit] Installer fails attempting to install Microsoft .NET Framework v. 4.5 (CQ-4218084).

  * (Mac) Manual script for removing desktop app files completely (CQ-4216489).

>[!NOTE]
>
>Issues found in AEM desktop app 1.7 beta loads that were absent in the 1.6 release are omitted from the release notes.

### Enhancements Available Since AEM desktop app 1.6 {#Enhancements-Available-Since-AEM-Desktop-App-16}

* Documentation: New [Best practices for v1.x app](/help/using/best-practices-for-v1.md) documentation.

* Improved login process to AEM:

  * Improve SAML handling * relax rules (CQ-4202781).

  * Add capability to configure a separate login URL in Preferences (CQ-4214052, CQ-4214051).

* Usability: Notify user when an asset is still downloading for larger assets (CQ-4216284).

* Networking:

  * DNS caching (CQ-4210176).

  * Support connection via proxy on Windows (CQ-4206854).

* Caching &amp; access to network share in Finder / Explorer:

  * The lock icon is now visible for checked out assets on Windows 10 (CQ-90957).

  * Folder content might disappear / reappear in network share (CQ-4209160, CQ-4210180).

  * Error on file upload due to a conflict reported in the Upload Queue Status (CQ-4215727).

  * While opening multiple files from desktop app folder in PS, file truncated or incomplete messages might be shown (CQ-4216276).

* Fixes in stability &amp; performance:

  * Improved performance while browsing folders with many assets (CQ-4214933).

  * The desktop app 1.5 can slow down a desktop machine over time (CQ-4209159).

  * Show queue status feature only work for the user who installed the app (CQ-4212199).

  * (Windows) Ensure that the 32-bit installer does not contain 64-bit code (CQ-4217406).

* Selected issues found &amp; fixed in 1.6 Beta:

  * High CPU usage (CQ-4218070).

  * Drag and Drop files yielding error when uploading to AEM (CQ-4217006).

### Enhancements Available Since AEM desktop app 1.5 {#Enhancements-Available-Since-AEM-Desktop-App-15}

**Version 1.5.1.5 for macOS X:** The 1.5.1.5 release provides the following benefits:

* New features and enhancement: Add Copy / Paste functionality to Finder integration to allow for direct transfer from Desktop to AEM (CQ-4208158).

* Bug fixes:

  * Fixed error 43 issue that occurred sometimes during asset renaming (CQ-4207900).

  * Reverting to an older version from the timeline in AEM does not update the asset in Finder (CQ-4205194).

  * desktop app crashes when browsing large nested directories (CQ-4208539).

  * desktop app mount point is now /Volumes/DAM so it's consistent for all users (CQ-4208159).

  * Placing a file into InDesign for the first time initiates an update warning (CQ-4207454).

Note on Link Warnings: Creative Cloud applications (such as InDesign) take a "snapshot" of the item's last-modified time at the time it is placed. If that date changes at a later point, the Adobe Creative Cloud app reports that the links are out-of-date. This information is reported in a couple of ways:

* When the Adobe Creative Cloud app is launched, it displays a dialog box informing the user that the linked assets are out of date, and prompt the user to take action.

* If the Adobe Creative Cloud app is already running, it shows a yellow triangle warning icon on the linked asset.

This behavior is the same for assets on local disk and assets in an AEM desktop mounted directory, with the following exceptions:

* If a different user edits a placed asset, then the warning icon shows up the first time that other users open a document containing the placed asset. This warning only happens if the placed asset has already been locally cached.

* If a user modifies a placed asset through the AEM desktop's mounted directory and then clears their local cache, then the placed asset is reported as out-of-date.

Both of these cases are expected and are side effects of the "delayed sync" architecture of AEM desktop.

**Version 1.5.0.x for macOS X and Windows:** This release of AEM desktop app provides the following benefits:

* Better stability and resilience against networking issues.

  * More stable mapping of AEM Assets folders (CQ-103276, CQ-4204669, CQ-4203957).

  * Better handling of cached files (CQ-4204336, CQ-4206263).

  * Improved handling of downloading / uploading of large files more than 2 GB in size (CQ-4206438).

  * Fixed "Error 36" when moving or renaming a larger number of files in Finder (CQ-4204640).

* Optimizations in network communication with AEM server (CQ-4204974, CQ-100903).

* Improved reliability of opening, placing, and saving assets from AEM in Creative Cloud apps (CQ-4203968, CQ-4205511, CQ-103543, CQ-4207141, CQ-90980).

* Improved supportability: option to clear cache (CQ-4202541), easy access to logs (CQ-4202340, CQ-4204673).

* Other fixes:
  * Better support for assets and folders having Japanese characters in name / non-English language settings (CQ-4195433, CQ-4205793, CQ-4199446).

  * Better log in handling with SSL (CQ-4200217).

  * More reliable share mounting (CQ-4200793).

  * Various improvements in stability (CQ-4207539, CQ-4200378).

  * Better handling of AEM Assets URL in Preferences (CQ-97388).

### Enhancements Available Since AEM desktop app 1.4 {#Enhancements-Available-Since-AEM-Desktop-App-14}

* Simplified upload of hierarchical folders through the new Create > Upload Folder action in Touch UI.
  * This action initiates a folder upload operation carried out by the desktop app.
  * Desktop app traverses the given folder hierarchy on the desktop in the background and uploads the files to AEM Assets.
  * User can monitor progress in the new Upload Queue Status window for ongoing operations.
  * The Upload Queue Status also provides better troubleshooting information (for example, no connection to the server).
* New Edit action in Touch UI that combines Checkout and Open operations into one.
* Optimized grouping of desktop-related actions in Touch UI (AEM 6.3).
* Improved compatibility with the latest OS releases.
* Customer reported fixes.

### Enhancements Available Since AEM desktop app 1.3 {#Enhancements-Available-Since-AEM-Desktop-App-13}

* Increased efficiency. Users spend less time waiting for network operations to complete.
* Improved Finder integration, which provides more stability and access to features, such as thumbnails.
* Caching and performance improvements.
* Better support for saving directly from desktop apps (PS, ID, AI, and so on).
* Improved integration with macOS (local network drive protocol changed from WebDAV to more stable SMB1).
* The desktop app connects with the AEM server using AEM native HTTP RESTful protocol.
* Files are saved locally first and then uploaded back to AEM in the background after a predefined time (30 sec). This workflow reduces the time to save files.
* Better handling of desktop applications that use intermediate file operations to save a file (partial saves and temporary files), which enables the AEM Asset timeline to display correct version and asset upload information.
* A dialog box is provided to track the status of background upload tasks.

## List of changes {#list-of-changes}

### Mount point on Mac {#mount-point-on-mac}

Since macOS 10.12 (Sierra), Apple has changed the permissions on the /Volumes folder that are used to mount network drives and devices to be more restrictive. Creating a new mount point at that location required administrative rights. This issue was fixed in macOS 10.12.5.

The AEM desktop app's mount point changed in versions 1.4 and 1.5. On macOS, it changed to a DAM sub-folder within the user's local folder, supporting non-admin users (CQ-104183).

Because the `/Volumes` folder no longer requires administrative rights, this change was reverted in 1.5.1. This change also makes it possible to share InDesign documents that have placed assets from AEM between macOS users.

### Protocol change (since v1.3) {#protocol-change-since}

* macOS X:
  * The local network drive protocol for OS X desktop integration changed to SMB1 from WebDAV.
  * The AEM repository mounted with the desktop app is visible as an `smb` network drive in the Finder, instead of a WebDAV drive.
* Windows:
  * The local network drive protocol for Windows desktop integrations stays; AEM is mounted as a WebDAV share.
* For both platforms (Windows and Mac):
  * The protocol to access / download assets and to upload changes to AEM has been changed to the native AEM protocol, which is an HTTP-based RESTful protocol. It provides greater control over network operations and is more compatible with the network infrastructure.

>[!NOTE]
>
>On macOS X, the change of local network drive protocol from WebDAV to SMB1 results in a different local path to the same asset in the repository. This change might impact links to files placed in Adobe Creative Cloud applications by way of the "Place" command. See the [Use AEM desktop app](use-app-v1.md) for more information.

### File handling (since 1.3) {#file-handling-since}

* Folders are updated automatically after a predefined delay (currently 30s). 
* Files checked out by other users are marked as read-only. 
* Files are saved to a network drive location mounted by way of the desktop app in two phases.
* In the first phase, a file is saved locally. This way, the user saving the file need not wait until the file is fully transferred to AEM, and can resume work as soon as the file is saved.
* In the second phase, the desktop app uploads an updated file to the AEM server after a predefined delay (for example, thirty seconds). This operation occurs in the background. Use the **Show Background File Sync Status** option to view the status of the upload operation.

## Important Notices {#important-notices}

**Folder Upload.** Adobe recommends that you use the new folder upload capability to upload larger, hierarchical folders into AEM. This approach is recommended as opposed to using a copy / drag-and-drop into a mounted AEM repository from Finder / Explorer level. When using the folder upload feature, the desktop app communicates with AEM directly and thus has much better control over the overall process.

**Keep AEM session available.** The AEM desktop app depends on a session open to the AEM Assets server to ensure proper operation. Daily users should unmount AEM Assets at day's end to log out, and remount in the morning to ensure login and network share functionality.

**Turn off "Icon Preview" in the Finder.** For performant browsing of large folders with Finder, especially with poor network connectivity, make sure that both "Icon" and "Icon Preview" are turned off. Otherwise, Finder starts downloading each asset in a folder to generate a small preview, which can lead to poor performance and high bandwidth utilization (CQ-4219779)

* In finder, go to AEM Assets shared network folder
* Right click on the DAM mount point
* Select Show View Options
* Unselect "Show icon preview"
* Click "Use as Defaults"

**Clean the cache when connecting to a new AEM server.** If the desktop app connects to another AEM server with the same URL, the cache is not cleared automatically. Clear the cache manually to ensure proper operations. Note that this process would typically happen in testing, when AEM installations can be replaced while running on the same URL (CQ-4216982)

**Use CA-signed SSL certificates.** The AEM desktop app does not support self-signed SSL certificates when connecting to AEM by way of an HTTPS secure connection. A CA-signed certificate is required on the server for such connections. (CQ-87941)

## Known issues {#known-issues}

* General:
  * Server URLs are required to point to the server without a path (for example, `http://server`, `https://server`, `http://server:port`, or `https://server:port`). Context paths and sub-folders other than /content/dam are not supported (CQ-89343, CQ-87272)
* File names / localization:
  * File and folder names with reserved characters are not properly handled. Make sure to use file and folder names that fit AEM requirements. (CQ-93361, CQ-93308, CQ-89276, CQ-4217183)
  * Some applications like Adobe Illustrator might create files with names not supported in AEM. For example, adding `Converted` after converting a file, which stops it from being uploaded. (CQ-4216985)
  * Assets with international names may appear and disappear every few seconds.
* Check in and Check out:
  * An asset checked out by one user is not possible to open for another user, either by Open action from Touch UI, or directly on the desktop. Some applications might report it as locked, but also corrupted or even hang while trying to open. (CQ-4199234)  
  * Changing files simultaneously by multiple users may cause some modifications to get lost. The workaround is to use the check-in and check-out functionality to prevent multiple users from changing the same file. (CQ-97035)
  * Certain applications do not support the read-only flag properly, which lets a user save a file that another user has checked out. The modified file is not transferred until the other user checks in the file. Both modifications are available in AEM as different versions of the asset. (CQ-89551, CQ-87572, CQ-89615)
  * The checked-out and read-only statuses are reported independently in the Finder. This approach results in two lock icons when a user checks out an asset. (CQ-89507)
* Finder integration:
  * When dragging and dropping large files, the Finder might time out while the files are being transferred in the background. This delay results in an `Error - 36`. The workaround is to drag-and-drop or open the asset again. (CQ-4219628)
  * Manual folder reload does not always work. Workaround: wait thirty seconds for the folder to be automatically updated. (CQ-97389)
  * More Asset Info... is limited to single file selections. (CQ-89542, CQ-87656)
  * Open in AEM Assets... is limited to single file and folder selections. (CQ-83382)
  * Error when renaming assets that have no extension. (CQ-4218971)
* Copy / Paste functionality: Paste is available when no asset has been copied to the clipboard.
* Windows:
  * Files with Alternate Data Streams (ADS) are only fully supported on NTFS. When copying files to the WebDAV share by way of the desktop app, a caution dialog box warns that some file properties cannot be transferred to the new location. This warning is usually fine because the properties are only relevant to a particular application on the user's desktop and have nothing to do with the actual file contents. (CQ-103770) (Win)
  * The user that is using the desktop app on Windows needs to be the one to install it. (CQ-4216389) (Win)
  * The app can crash when selecting the [!UICONTROL Retry] option on a failed upload. This crash can occur under certain circumstances after having resumed batch upload when disconnected. (CQ-4251884) (Win)

## Helpful resources {#helpful-resources}

* [AEM Documentation](https://experienceleague.adobe.com/en/docs)
* [Use AEM desktop app v1.x](use-app-v1.md)
* [AEM desktop app v1.x best practices](best-practices-for-v1.md)

## Compatibility matrix and prerequisites {#compatibilitymatrix}

AEM desktop app works with various versions of AEM. See the compatibility matrix for the supported versions.

| Version | Revision | Release Date | Compatibility |
|--- |--- |--- |--- |
| 1.10 | 1.10.0.3 (Mac and Win) | August 31, 2018 | AEM 6.5; AEM 6.4 SP1; AEM 6.3 SP2; AEM 6.2 SP1 CFP2+; AEM 6.1 SP2 CFP7+ |
| 1.9 | 1.9.1.1 (Mac and Win) | June 21, 2018 | AEM 6.4; AEM 6.3 SP1; AEM 6.2 SP1 CFP2+; AEM 6.1 SP2 CFP7+ |
| 1.8 | 1.8.1.0 (Mac and Win) | March 28, 2018 | AEM 6.4; AEM 6.3 SP1; AEM 6.2 SP1 CFP2+; AEM 6.1 SP2 CFP7+ |
| 1.7 | 1.7.0.3 (Mac and Win) | January 10, 2018 | AEM 6.3 SP1; AEM 6.2 SP1 CFP2+; AEM 6.1 SP2 CFP7+ |
