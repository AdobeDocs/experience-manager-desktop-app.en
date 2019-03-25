---
title: AEM Desktop App Release Notes
seo-title: AEM Desktop App Release Notes
description: Release notes specific to Desktop App Adobe Experience Manager 6.3 Assets.
seo-description: Release notes specific to Desktop App Adobe Experience Manager 6.3 Assets.
uuid: b783c3f8-aa1e-4c05-b687-5894909769f5
contentOwner: asgupta
topic-tags: release-notes
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4
discoiquuid: 3052549b-fe75-44fb-a55e-5cc612868f54
index: y
internal: n
snippet: y
---

# AEM Desktop App Release Notes{#aem-desktop-app-release-notes}

## Release Information {#release-information}

| Products      |  Adobe Experience Manager (AEM) Desktop App                                                                                                                                                                                                            |
|---------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Version       | 1.10 (1.10.0.3 on Mac and Windows)                                                                                                                                                                                                                     |
| Type          | Minor release                                                                                                                                                                                                                                          |
| Date          | August 31, 2018                                                                                                                                                                                                                                        |
| Download URLs |  <ul><li>Mac OS X 64 bit</li><li>Windows 32 bit</li><li>Windows 64 bit</li></ul> **Note:** If you downloaded the installer before September 5, 2018, ensure that you are using the v1.10 of the pap. Double check the binary's version and re-download if needed. The links on this page were stale before.  |
| Compatibility | <ul><li>AEM 6.4 SP1</li><li>AEM 6.3 SP2</li><li>AEM 6.2 SP1 CFP2+</li><li>AEM 6.1 SP2 CFP7+</li></ul>                                                                                                                                                                                   |

>[!NOTE]
>
>Cache size limit is not enforced. When the desktop app starts, the cache size is calculated once, and a notification is shown if the size is close to the predefined limit.

## System requirements and prerequisites {#system-requirements-and-prerequisites}

AEM Desktop is compatible with the following operating systems:

* Mac OS X 10.10 or later, with latest bug fixes.
* Windows 7 and Windows 10 with the latest service packs and bug fixes.

Adobe strongly recommends using the latest version of AEM Desktop to avail the latest functionality, the most recent bug fixes, and the best possible performance.

The version of AEM Destkop App you are planning to install on your local machine requires a specific AEM server version/additional server-side components (service packs, hot fixes or feature packs). Ensure that the AEM server is properly configured before you connect to it for the first time. If you require help, contact your AEM administrator.

See the [detailed compatibility matrix](#compatibilitymatrix) at the end of this document to evaluate the prerequisites for your setup.

## What's New in AEM Desktop App 1.10 {#what-s-new-in-aem-desktop-app}

AEM Desktop App 1.10 focuses on improving user experience around large uploads, information about the background operations, and optimized experience when opening assets with linked files (like InDesign).

**Local Editing / Check-Out**

Automatic uploads of changes saved to assets can be disabled in the status window. That way the user can continue working on files and saving changes and then, when they are ready, decide to upload all changes.

**Simplified Asset Status Window**

The status window was simplified - Uploads tab now shows both individual assets, as well as folder / bulk uploads. The previous Bulk Uploads tab was removed.

**Application Icon to Indicate Bulk Uploads**

The application icon will indicate that a bulk upload is in progress by showing a "transfer" overlay.

**Notifications for Update Conflicts**

When the application detects a conflict when trying to update an asset, it will show a notification, so that the user can review that without the need to monitor the status window. When the application starts, it will check for all the conflicts, so that the user can resolve them.

**Better Handling of Connection Losses**

Bulk uploads will be paused if there is a connection loss, and the user will be able to resume later. A Retry button is availble to retry a failed upload of an individual file.

## Installation instructions {#installation-instructions}

For detailed instructions, see [Install and configure AEM Desktop App](install-configure-app-v1.md).

## Enhancements in the previous versions {#enhancements-in-the-previous-versions}

<!--
Comment Type: draft

<p>AEM Desktop App 1.9 focuses on improved upload experience with resumable uploads, better indication of status of the background operations with a new Asset Status UI and application icon, as well as better experience when opening files with linked assets, like InDesign files, with linked assets pre-fetching to the local cache. Documentation has been split into User Guide and Configuration Guide to better serve the needs of end users and admins, respectively.</p>
-->

This release extends and replaces the previous versions of the Experience Manager Desktop App, which provided the following key enhancements:

* Version 1.9/1.9.1: resumable uploads, improved status window, application icons indicating status of application / connection, pre-fetching of linked assets for InDesign files
* Version 1.8: better control of cache size for the user, improved login experience for SAML/SSO on Windows, supporting .pac network proxy on Mac, and customer-reported issues.
* Version 1.7: improvements in stability and caching logic, better support for network proxy, and ability to clean up internal files after uninstallation.
* Version 1.6: improvements in the login process for various AEM security configurations and application stability and performance.  
* Version 1.5: application stability and resilience against various networking problems, better supportability.  
* Version 1.4: the ability to upload hierarchical folders in the background with the progress monitoring. 
* Version 1.3: performance enhancements and stability of accessing files and saving changes to AEM, especially from Creative Cloud desktop applications, such as InDesign, Illustrator, or Photoshop. It aimed to provide users with a more local desktop-like experience when working with files, while simultaneously handling network data transfer operations in the background.

<details> 
 <summary>Enhancements Available Since AEM Desktop App 1.9.x</summary> 
 <p>Adobe Experience Manager (AEM) Desktop App 1.9.1 was a patch release to addresses a few key customer issues around asset checkout and copying files from network share to a local directory. </p> 
 <ul> 
  <li>Assets checked out by one users should not be available for modification for other users (CQ-4246009)</li>
  <li>Support copy from mapped folder to a local folder when user folder is on a separate disk partition (CQ-4243978)</li>
 </ul>
 <p>AEM Desktop App 1.9 focused on improving user experience around large uploads, information about the background operations, and optimized experience when opening assets with linked files (like InDesign).</p> 
 <p><strong>Resumable Uploads</strong></p> 
 <p>For uploads, especially around large files, there is an option to pause/resume them in the new Asset Status window.</p> 
 <p><strong>Improved Asset Status Window</strong></p> 
 <p>An improved asset status window provides information about assets that are:</p> 
 <p>Changes</p> 
 <ul> 
  <li>Displays currently queued changes</li>
  <li>Shows in-progress uploads, including a progress bar, transfer rate, total file size, and size transferred so far</li>
  <li>Completed uploads shown with total transferred and final rate</li>
  <li>Failed uploads display along with an error message and transfer information, if available</li>
  <li>Uploads that have failed 3 times will show an error message</li>
  <li>Conflicting files shown with an icon that the user can click. Clicking the icon shows a dialog with an explanation and two options: 
   <ul> 
    <li>"Keep Mine": immediately uploads the file to the server</li>
    <li>"Overwrite Mine": immediately deletes the local file and downloads a new copy from the server</li>
   </ul></li>
 </ul>
 <p>Downloads</p> 
 <ul> 
  <li>Displays in-progress downloads, including a transfer rate and size transferred so far</li>
  <li>Completed downloads shown with total transferred, final rate, and an icon that will open the file when clicked (only available for single files)</li>
  <li>Failed downloads displayed with an error message and transfer information, if available</li>
  <li>Footer shows total number of files downloaded and average transfer rate</li>
  <li>If a user chooses to open or edit multiple files from the AEM Assets Web UI, they will be grouped together, showing up as e.g. "myasset.jpeg and 4 more file(s)"</li>
  <li>When downloading InDesign Documents including linked assets that are stored in AEM Assets, the Desktop App will download all of the linked Assets first, before opening the InDesign Document and indicate the download of linked assets as e.g. (5 of 24)</li>
 </ul>
 <p>Bulk Uploads</p> 
 <p>uploading large folder hierarchies via Create &amp;gt; Upload Folder in AEM web UI or copying and selecting "Paste Assets" in Finder/Explorer in the Desktop App context menu will trigger usage of this dialog</p> 
 <ul> 
  <li>Displays in-progress uploads, including a progress bar and the name of the file currently being transferred</li>
  <li>In-progress uploads include an icon that will cancel the upload when clicked. The transfer will stop after the currently transferring file completes</li>
  <li>Failed transfer processes are displayed with an error message (only if the entire transfer fails)</li>
  <li>If an individual file fails to transfer, it will show up on the tab as an error. Otherwise, individual files will not show on the tab - only a single entry for the entire upload.</li>
 </ul>
 <p><strong>Icons to Indicate Status of Background Operations</strong></p> 
 <p>The application icon will indicate the state of background operations to provide better visual cue to the users. E.g., when the application is not connected to AEM the icon will be grayed out, when there is an active upload it will show a "sync" overlay, etc.</p> 
 <p><strong>Pre-fetching of Linked Assets</strong></p> 
 <p>To improve user expereince when working with InDesign documents which include linked assets stored in AEM, desktop app will try and pre-fetch these linked files to local cache before it downloads and opens the InDesign document. That way the user will have the linked files available locally, and won't have to wait longer when accessing these in InDesign (in the Links panel).</p> 
 <p>Please note that prefetching only works if AEM recognizes the links on the server side. An asset with recognized links will have a list of "References" listed in the Properties view of the InDesign asset.</p> 
</details>

<details> 
 <summary>Enhancements Available Since AEM Desktop App 1.8.x</summary> 
 <p>AEM Desktop App 1.8.1 fast-follow release added improvements when opening multiple files at once from AEM UI to the 1.8 release (CQ-4237747, CQ-4238780).</p> 
 <p>Enhancements in AEM Desktop App 1.8:</p> 
 <ul> 
  <li>Caching 
   <ul> 
    <li>new UI for managing AEM Desktop App cache (CQ-4208690), including 
     <ul> 
      <li>view current cache size</li>
      <li>define maximum cache size before a notification is send</li>
      <li>Cache size is checked on Desktop App start only, and a notification is shown if it is reaching the configured limit</li>
      <li>clearing cache button is now available in the new UI</li>
     </ul></li>
   </ul></li>
  <li>Login 
   <ul> 
    <li>[Win] Fixed login to AEM instance configured to use SAML and SSL (CQ-4216353)</li>
   </ul></li>
  <li>Network 
   <ul> 
    <li>when an AEM session expires, user is now notified and can click on the notification to log in again (CQ-4202028)</li>
    <li>[Mac] Add support for connecting to AEM via using .pac proxy configuration (CQ-4233430)</li>
    <li>[Win] fix issues with Advanced -&amp;gt; Login URL dialog (CQ-4236061)</li>
   </ul></li>
  <li>Bugfixes 
   <ul> 
    <li>More Asset Info dialog - sometimes action bar was not visible (CQ-4208540)</li>
    <li>[Win] File can now be synchronized after reverting to a previous version from AEM Assets UI (CQ-4216411)</li>
   </ul></li>
 </ul>
</details>

<details> 
 <summary>Enhancements Available Since AEM Desktop App 1.7</summary> 
 <ul> 
  <li>Stability 
   <ul> 
    <li>Improved stability when AEM Desktop App connects to an overloaded AEM server (CQ-4224803)</li>
    <li>Improved stability when many files are requested (CQ-4224212)</li>
    <li>Improved asset update with additional check (CQ-4228291)</li>
   </ul></li>
  <li>Caching 
   <ul> 
    <li>Fix disk errors and opening problems when opening files in Photoshop, InDesign, Finder (CQ-4223993, CQ-4217603, CQ-4223717)</li>
    <li>Improved caching to avoid zero-size binaries (CQ-4216599)</li>
   </ul></li>
  <li>Login 
   <ul> 
    <li>Allow for connecting with strictSSL disabled for special configurations (like locally-issued certificates) (CQ-4223949)</li>
   </ul></li>
  <li>Networking 
   <ul> 
    <li>Improved support for connecting over network proxy (CQ-4223477, CQ-4221280, CQ-4206854)</li>
   </ul></li>
  <li>Installation / uninstallation 
   <ul> 
    <li>[Windows] Cleaner uninstallation (CQ-4220906)</li>
    <li>[Windows 32bit] Installer fails attempting to install Microsoft .NET Framework v. 4.5 (CQ-4218084)</li>
    <li>[Mac] Manual script for removing Desktop App files completely (CQ-4216489)</li>
   </ul></li>
 </ul>
 <note type="note"> 
  <p>Issues found in AEM Desktop App 1.7 beta loads (that weren’t present in the 1.6 release are not reported in the release notes). Beta testers can review status of these issues in the AEM Desktop App prerelease program.</p> 
 </note> 
</details>

<details> 
 <summary>Enhancements Available Since AEM Desktop App 1.6</summary> 
 <ul> 
  <li>Documentation 
   <ul> 
    <li>New <a href="https://helpx.adobe.com/experience-manager/6-3/assets/using/aem-desktop-app-best-practices.html">AEM Desktop App Best Practices</a> documentation</li>
   </ul></li>
  <li>Improved login process to AEM: 
   <ul> 
    <li>Improve SAML handling - relax rules (CQ-4202781)</li>
    <li>Add capability to configure separate login URL in Preferences (CQ-4214052, CQ-4214051)</li>
   </ul></li>
  <li>Usability 
   <ul> 
    <li>Notify user when asset is still downloading for larger assets (CQ-4216284)</li>
   </ul></li>
  <li>Networking 
   <ul> 
    <li>DNS caching (CQ-4210176)</li>
    <li>Support connection via proxy on Windows (CQ-4206854)</li>
   </ul></li>
  <li>Caching &amp; access to network share in Finder / Explorer 
   <ul> 
    <li>Lock icon now visible for checked out assets on Windows 10 (CQ-90957)</li>
    <li>Folder content might disappear/reappear in network share (CQ-4209160, CQ-4210180)</li>
    <li>Error on file upload due to a conflict reported in the Upload Queue Status (CQ-4215727)</li>
    <li>While opening multiple files from desktop app folder in PS, file truncated or incomplete messages might be shown (CQ-4216276)</li>
   </ul></li>
  <li>Fixes in stability &amp; performance 
   <ul> 
    <li>Improved performance while browsing folders with many assets (CQ-4214933)</li>
    <li>Desktop App 1.5 can slow down desktop machine over time (CQ-4209159)</li>
    <li>Show queue status feature only work for the user who installed the app (CQ-4212199)</li>
    <li>(Windows) Ensure that 32-bit installer does not contain 64-bit code (CQ-4217406)</li>
   </ul></li>
  <li>Selected issues found &amp; fixed in 1.6 Beta 
   <ul> 
    <li>High CPU usage (CQ-4218070)</li>
    <li>Drag and Drop files yielding error when uploading to AEM (CQ-4217006)</li>
   </ul></li>
 </ul>
</details>

<details> 
 <summary>Enhancements Available Since AEM Desktop App 1.5</summary> 
 <p><strong>Version 1.5.1.5 for Mac OS X:</strong></p> 
 <p>The 1.5.1.5 release provides the following benefits:</p> 
 <ul> 
  <li>New features and enhancements: 
   <ul> 
    <li>Add Copy/Paste functionality to Finder integration to allow for direct transfer from Desktop to AEM (CQ-4208158)</li>
   </ul></li>
  <li>Bugfixes: 
   <ul> 
    <li>Fixed error 43 issue that occurred sometimes during asset renaming (CQ-4207900)</li>
    <li>Reverting to an older version from the timeline in AEM does not update the asset in Finder (CQ-4205194) </li>
    <li>Desktop App crashes when browsing large nested directories (CQ-4208539)</li>
    <li>Desktop App mount point is now /Volumes/DAM so it’s consistent for all users (CQ-4208159)</li>
    <li>Placing file into InDesign for the first time initiates an update warning (CQ-4207454)</li>
   </ul></li>
 </ul>
 <p><em>Note on Link Warnings</em></p> 
 <p>Creative Cloud applications (such as InDesign) take a "snapshot" of the item's last-modified time at the time it is placed. If that date changes at a later point, the CC app will report that the links are out-of-date. This is reported in a couple of ways:</p> 
 <ul> 
  <li>When the CC app is launched, it will display a dialog informing the user that the linked assets are out of date, and prompt the user to take action</li>
  <li>If the CC app is already running, it will show a yellow triangle warning icon on the linked asset</li>
 </ul>
 <p>This behavior is the same for assets on local disk and assets in an AEM Desktop mounted directory, with the following exceptions:</p> 
 <ul> 
  <li>If a placed asset is modified by a different user, then the warning icon will show up the first time that other users open a document containing the placed asset. This will only happen if the placed asset has already been locally cached</li>
  <li>If a user modifies a placed asset through AEM desktop's mounted directory and then clears their local cache, then the placed asset will be reported as out-of-date</li>
 </ul>
 <p>Both of these cases are expected and are side effects of the "delayed sync" architecture of AEM Desktop. </p> 
 <p><strong>Version 1.5.0.x for Mac OS X and Windows:</strong></p> 
 <p>This release of AEM Desktop App provides the following benefits:</p> 
 <ul> 
  <li>Better stability &amp; resilience against networking issues 
   <ul> 
    <li>More stable mapping of AEM Assets folders (CQ-103276, CQ-4204669, CQ-4203957)</li>
    <li>Better handling of cached files (CQ-4204336, CQ-4206263)</li>
    <li>Improved handling of downloading/uploading of large files &amp;gt;2GB (CQ-4206438)</li>
    <li>Fixed "Error 36" when moving or renaming a larger number of files in Finder (CQ-4204640)</li>
   </ul></li>
  <li>Optimizations in network communication with AEM Server (CQ-4204974, CQ-100903)</li>
  <li>Improved reliability of opening, placing, and saving AEM assets in Creative Cloud apps (CQ-4203968, CQ-4205511, CQ-103543, CQ-4207141, CQ-90980)<br /> </li>
  <li>Improved supportability: option to clear cache (CQ-4202541), easy access to logs (CQ-4202340, CQ-4204673)</li>
  <li>Other fixes 
   <ul> 
    <li>Better support for assets &amp; folders having Japanese characters in name / non-English language settings (CQ-4195433, CQ-4205793, CQ-4199446)</li>
    <li>Better handling of login with SSL (CQ-4200217)</li>
    <li>More reliable share mounting (CQ-4200793)</li>
    <li>Various improvements in stability (CQ-4207539, CQ-4200378)</li>
    <li>Better handling of AEM Assets URL in Preferences (CQ-97388)</li>
   </ul></li>
 </ul>
</details>

<details> 
 <summary>Enhancements Available Since AEM Desktop App 1.4</summary> 
 <ul> 
  <li>Simplified upload of hierarchical folders through the new Create &amp;gt; Upload Folder action in Touch UI
   <ul>
    <li>Action initiates a folder upload operation carried out by the Desktop App</li>
    <li>Desktop app traverses the given folder hierarchy on desktop in the background and uploads the files to AEM Assets</li>
    <li>User can monitor progress in the new Upload Queue Status window with progress bar for ongoing operations</li>
    <li>The Upload Queue Status also provides better troubleshooting information (e.g., no connection to server)</li>
   </ul></li>
  <li>New Edit action in Touch UI, that combines Check out and Open operations into one</li>
  <li>Optimized grouping of desktop-related actions in Touch UI (AEM 6.3)</li>
  <li>Improved compatibility with the latest OS releases</li>
  <li>Customer reported fixes</li>
 </ul>
</details>

<details> 
 <summary>Enhancements Available Since AEM Desktop App 1.3</summary>
 <ul>
  <li>Increased efficiency. Users spend less time waiting for network operations to complete.</li>
  <li>Improved Finder integration, which provides more stability and access to features, such as thumbnails.</li>
  <li>Caching and performance improvements.</li>
  <li>Better support for saving directly from desktop apps (PS, ID, AI, and so on).</li>
  <li>Improved integration with Mac OS (local network drive protocol changed from WebDAV to more stable SMB1)</li>
  <li>Desktop app connects with the AEM server using AEM native HTTP RESTful protocol</li>
  <li>Files are saved locally first and then uploaded back to AEM in the background after a predefined time (30 sec). This reduces the time to save files.</li>
  <li>Better handling of desktop applications that use intermediate file operations to save a file (partial saves and temporary files), which enables the AEM Asset timeline to display correct version and asset upload information.</li>
  <li>Dialog provided to track the status of background upload tasks.</li>
 </ul>
</details>

## List of changes {#list-of-changes}

### Mount Point on Mac {#mount-point-on-mac}

Since MacOS 10.12 (Sierra), Apple has changed the permissions on the /Volumes folder used to mount network drives and devices to more restrictive. Creating a new mount point there required administrative rights. This issue was fixed in MacOS 10.12.5.

As AEM Desktop App should run for users who do not have admin rights on the local machine, the mount point for AEM Assets repository was changed in 1.4 and 1.5 to a DAM subfolder in user's local folder on MacOS (CQ-104183).

Since the /Volumes folder no longer requires administrative rights, this change was reverted in 1.5.1. This also makes it possible to share InDesign documents that have placed AEM assets between MacOS users.

### Protocol change (Since 1.3) {#protocol-change-since}

* Mac OS X

  * The local network drive protocol for OS X desktop integration changed to SMB1 from WebDAV.
  * The AEM repository mounted with Desktop App will be visible as an “  smb ” network drive in Finder, instead of a WebDAV drive.

* Windows

  * The local network drive protocol for Windows desktop integrations stays; AEM will be mounted as a WebDAV share

* For both platforms (Windows and Mac)

  * The protocol to access/download assets and to upload changes to AEM has been changed to the native AEM protocol, which is an HTTP-based RESTful protocol. It provides greater control over network operations and is more compatible with the network infrastructure.

>[!NOTE]
>
>On Mac OS X, the change of local network drive protocol from WebDAV to SMB1 results in a different local path to the same asset in the repository. This might impact links to files placed in CC applications via "Place" command. See the [documentation](use-app-v1.md) for more information.

### File handling (since 1.3) {#file-handling-since}

* Folders are updated automatically after a predefined delay (currently 30s). 
* Files checked out by other users are marked as read-only. 
* Files are saved to a network drive location mounted via Desktop App in two phases.
* In the first phase, a file is saved locally. This way, the user saving the file need not wait until the file is fully transferred to AEM, and can resume work as soon as the file is saved.
* In the second phase, Desktop App uploads an updated file to AEM server after a predefined delay (for example,  30s ). This operation occurs in the background. Use the **Show Background File Sync Status** option to view the status of the upload operation.

## Important Notices {#important-notices}

**Folder Upload.** It is recommended to use the new Folder Upload capability to upload larger, hierarchical folders into AEM as opposed to using a copy / drag and drop into a mounted AEM repository from Finder / Explorer level. When using the folder upload feature, Desktop App communicates with AEM directly and thus has much better control over the overall process.

**Keep AEM session available.** AEM Desktop App depends on a session open to AEM Assets server to ensure proper operation. For users working with Desktop App every day, it is recommended to Unmount AEM Assets at the end of their day to force log out, and then "Mount AEM Assets" in the morning to ensure they're logged in and the network share is operational.

**Turn off "Icon Preview" in Finder.** For performant browsing of large folders with Finder, especially with poor network connectivity, make sure that both "Icon" and "Icon Preview" is turned off. Otherwise, Finder will start downloading each asset in a folder to generate a small preview, which can lead to poor performance and high bandwidth utilization (CQ-4219779)

* In finder, go to AEM Assets shared network folder
* Right click on the DAM mount point
* Select Show View Options
* Unselect "Show icon preview"
* Click "Use as Defaults"

**Clean cache when connecting to a new AEM server. **If Desktop App connects to another AEM server with the same URL, cache is not cleared automatically. Clear cache manually to ensure proper operations. Note this would typically happen in testing, when AEM installations can be replaced while running on the same URL (CQ-4216982)

**Use CA-signed SSL certificates.** Please note that AEM Desktop App doesn't support self-signed SSL certificates when connecting to AEM via a HTTPS secure connection. A CA-signed certificate is required on the server for such connections. (CQ-87941)

## Known issues {#known-issues}

* General

    * Server URLs are required to point to the server without a path (e.g. *http://server*, *https://server*, *http://server:port*, or *https://server:port*). Context paths and sub-folders other than /content/dam are not supported (CQ-89343, CQ-87272)

* File names / localization

    * File and folder names with reserved characters are not properly handled. Make sure to use file and folder names that fit AEM requirements (CQ-93361, CQ-93308, CQ-89276, CQ-4217183)
    * Some applications like Adobe Illustrator might create files with names not supported in AEM - e.g., adding "[Converted]" after converting a file, which stops it from being uploaded (CQ-4216985)
    * Assets with international names may appear and disappear every few seconds

* Checkin/Checkout

    * An asset checked out by one user is not possible to open for another user, either by Open action from Touch UI, or directly on the desktop. Some applications might report it as locked, but also corrupted or even hang while trying to open. (CQ-4199234)  
    * Changing files simultaneously by multiple users may cause some modifications to get lost. The workaround is to use the  checkin /checkout functionality to prevent multiple users from changing the same file (CQ-97035)
    * Certain applications don't support the read-only flag properly which allows a user to save a file that's checked out by another user. The modified file is not transferred until the other user checks in the file. Both modifications are available in AEM as different versions of the asset (CQ-89551, CQ-87572, CQ-89615)
    * The checked-out and read-only status are reported independently in Finder. This results in 2 lock icons when a user checks out an asset (CQ-89507)

* Finder integration

    * When dragging/dropping large files, Finder might time out while files are being transferred in the background. This results in an "Error -36." The workaround is to drag/drop or open the asset again (CQ-4219628)
    * Manual folder reload does not always work. Workaround:  wait   30s  for the folder to be automatically updated. (CQ-97389)
    
    * More Asset Info... is limited to single file selections (CQ-89542, CQ-87656)
    * Open in AEM Assets... is limited to single file and folder selections (CQ-83382)
    * Error when renaming assets that have no extension (CQ-4218971)

* Copy/Paste functionality

    * Paste is available when no asset has been copied to the clipboard

* Windows

    * Files with Alternate Data Streams (ADS) are only fully supported on NTFS. Copying such files to the WebDAV share provided by the Desktop App will result in a caution dialog warning the user that the file has properties that can't be copied to the new location. This is usually fine since the properties are only relevant to a particular application on the user's desktop and have nothing to do with the actual file contents (CQ-103770) [win]
    * Desktop App on Windows needs to be installed by the user that will be using it (CQ-4216389) [win]
    * The app can crash when clicking the Retry button on a failed upload under certain circumstances - after having resumed batch upload when disconnected (CQ-4251884) [win]

<!--
Comment Type: annotation
Last Modified By: ims-author-230927A44C16A40C0A04B82A@AdobeID
Last Modified Date: 2017-06-23T13:13:38.564-0400
Update for 1.5 - GK - done - cleaned up resolved issues, added 1.5.1 relevant open issues - Bob/Team - TBD Updated for 1.5.1 - Removed InDesign update warning issue - Removed Disconnect issue error 43 - Removed relink issue - Removed desktop app crash issue using large folder
-->

## Helpful resources {#helpful-resources}

* [AEM Documentation](https://helpx.adobe.com/support/experience-manager/6-4.html)
* [Use AEM Desktop App v1.x](use-app-v1.md)
* [AEM Desktop App v1.x best practices](best-practices-for-v1.md)

## Compatibility matrix and prequisites {#compatibilitymatrix}

AEM Desktop App works with various verisons of AEM. See the compatibility matrix for the supported versions.

| Version | Revision               | Release Date | Compatibility                                               |
|---------|------------------------|--------------|-------------------------------------------------------------|
| 1.10    | 1.10.0.3 (Mac and Win) | Aug 31, 2018 | <ul><li>AEM 6.4 SP1</li><li>AEM 6.3 SP2</li><li>AEM 6.2 SP1 CFP2+</li><li>AEM 6.1 SP2 CFP7+</li></ul> |
| 1.9     | 1.9.1.1 (Mac and Win)  | Jun 21, 2018 | <ul><li>AEM 6.4</li><li>AEM 6.3 SP1</li><li>AEM 6.2 SP1 CFP2+</li><li>AEM 6.1 SP2 CFP7+</li></ul>     |
| 1.8     | 1.8.1.0 (Mac and Win)  | Mar 28, 2018 | <ul><li>AEM 6.4</li><li>AEM 6.3 SP1</li><li>AEM 6.2 SP1 CFP2+</li><li>AEM 6.1 SP2 CFP7+</li></ul>     |
| 1.7     | 1.7.0.3 (Mac and Win)  | Jan 10, 2018 | <ul><li>AEM 6.3 SP1</li><li>AEM 6.2 SP1 CFP2+</li><li>AEM 6.1 SP2 CFP7+</li></ul>             |

<!-->
<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody> 
  <tr> 
   <td><p><strong>Version</strong></p> </td> 
   <td><p><strong>Revision</strong></p> </td> 
   <td><p><strong>Release Date</strong></p> </td> 
   <td><p><strong>Compatibility</strong></p> </td> 
  </tr> 
  <tr> 
   <td><strong>1.10</strong></td> 
   <td><strong>1.10.0.3 (Mac &amp; Win)</strong></td> 
   <td><strong>August 31, 2018</strong></td> 
   <td><p><strong>AEM 6.4 SP1</strong></p> <p><strong>AEM 6.3 SP2</strong></p> <p><strong>AEM 6.2 SP1 CFP2+</strong></p> <p><strong>AEM 6.1 SP2 CFP7+</strong></p> </td> 
  </tr> 
  <tr> 
   <td><strong>1.9</strong></td> 
   <td>1.9.1.1 (Mac &amp; Win)</td> 
   <td>June 21, 2018</td> 
   <td><p>AEM 6.4</p> <p>AEM 6.3 SP1</p> <p>AEM 6.2 SP1 CFP2+ </p> <p>AEM 6.1 SP2 CFP7+</p> </td> 
  </tr> 
  <tr> 
   <td><strong>1.8</strong></td> 
   <td>1.8.1.0 (Mac &amp; Win)</td> 
   <td>March 28, 2018</td> 
   <td><p>AEM 6.4</p> <p>AEM 6.3 SP1</p> <p>AEM 6.2 SP1 CFP2+ </p> <p>AEM 6.1 SP2 CFP7+</p> </td> 
  </tr> 
  <tr> 
   <td><p><strong>1.7</strong></p> </td> 
   <td><p>1.7.0.3 (Mac, Win)</p> </td> 
   <td><p>January 10, 2018</p> </td> 
   <td><p>AEM 6.3 SP1</p> <p>AEM 6.2 SP1 CFP2+</p> <p>AEM 6.1 SP2 CFP7+</p> </td> 
  </tr> 
  <tr> 
   <td><p><strong>1.6</strong></p> </td> 
   <td><p>11.6.0.8 (Mac)</p> <p>1.6.0.12 (Win)</p> </td> 
   <td><p>September 29, 2017</p> </td> 
   <td><p>AEM 6.3</p> <p>AEM 6.2 SP1 (with Hot Fix 11099 applied)</p> <p><a href="https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq610/servicepack/AEM-6.1-Service-Pack-2">AEM 6.1 SP2</a> (with <a href="https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq610/featurepack/cq-6.1.0-featurepack-6658">Feature Pack 6658</a> and <a href="https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq610/hotfix/cq-6.1.0-hotfix-8723">Hot Fix 8723</a> applied)</p> </td> 
  </tr> 
  <tr> 
   <td><p><strong>1.5</strong></p> </td> 
   <td><p>1.5.1.5 (Mac)</p> <p>1.5.0.3 (Win)</p> </td> 
   <td><p>June 23, 2017</p> <p>May 31, 2017</p> </td> 
   <td><p>AEM 6.3</p> <p>AEM 6.2 SP1 (with Hot Fix 11099 applied)</p> <p><a href="https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq610/servicepack/AEM-6.1-Service-Pack-2">AEM 6.1 SP2</a> (with <a href="https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq610/featurepack/cq-6.1.0-featurepack-6658">Feature Pack 6658</a> and <a href="https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq610/hotfix/cq-6.1.0-hotfix-8723">Hot Fix 8723</a> applied)</p> </td> 
  </tr> 
  <tr> 
   <td><p><strong>1.4</strong></p> </td> 
   <td><p>1.4.0.1 (Mac)</p> <p>1.4.0.3 (Win)</p> </td> 
   <td><p>February 28, 2017</p> </td> 
   <td><p>AEM 6.3</p> <p>AEM 6.2 SP1 (with Hot Fix 11099 applied)</p> <p><a href="https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq610/servicepack/AEM-6.1-Service-Pack-2">AEM 6.1 SP2</a> (with <a href="https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq610/featurepack/cq-6.1.0-featurepack-6658">Feature Pack 6658</a> and <a href="https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq610/hotfix/cq-6.1.0-hotfix-8723">Hot Fix 8723</a> applied)</p> </td> 
  </tr> 
  <tr> 
   <td><p><strong>1.3</strong></p> </td> 
   <td><p>1.3.1.17 (Mac)</p> <p>1.3.13 (Win)</p> </td> 
   <td><p>September 16, 2016</p> <p>November 14, 2016</p> </td> 
   <td><p>AEM 6.2 (with <a href="https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq620/hotfix/cq-6.2.0-hotfix-11099">Hot Fix 11099</a> applied)</p> <p><a href="https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq610/servicepack/AEM-6.1-Service-Pack-2">AEM 6.1 SP2</a> (with <a href="https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq610/featurepack/cq-6.1.0-featurepack-6658">Feature Pack 6658</a> and <a href="https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq610/hotfix/cq-6.1.0-hotfix-8723">Hot Fix 8723</a> applied)</p> </td> 
  </tr>
 </tbody>
</table>
<--!>