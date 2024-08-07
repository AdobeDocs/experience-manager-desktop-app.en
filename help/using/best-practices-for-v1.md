---
title: Desktop app v1.10 best practices
description: Key capabilities and recommended use of [!DNL Adobe Experience Manager] desktop app version 1.10.
exl-id: 5de06b33-c05c-47eb-b884-408b6f9afc94
---
# AEM desktop app v1.10 best practices {#aem-desktop-app-best-practices}

## Overview {#overview}

[!DNL Adobe Experience Manager] desktop app links your Digital Asset Management (DAM) solution with your desktop so you can open the files that are available in the AEM Web UI directly on the desktop. If you saved an asset from the desktop, it is uploaded to AEM at the appropriate location.

AEM desktop app eliminates the chances of you updating incorrect local copies or updating a wrong asset in AEM. The desktop app's easy-to-use workflow is enabled using network share technology that desktop operating systems provide.

The desktop app mounts the AEM Assets repository as a network share on the desktop. Therefore, the folders and files appear as if they were local. However, it is not recommended to carry out digital asset management operations directly from the desktop in the mounted network share in Finder or Explorer. Instead, Adobe recommends that you use AEM Assets Web UI to perform operations, such as copying or moving a large number of assets.

>[!NOTE]
>
>Before reading this document, you can review the overall [AEM and Creative Cloud integration best practices](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/administer/aem-cc-integration-best-practices) for a higher-level overview of the topic.

## AEM desktop app architecture {#aem-desktop-app-architecture}

AEM desktop app uses WebDAV (Windows) or SMB (Mac) network shares to mount network shares. The mounted network share is local only. AEM desktop app intercepts the calls (open, read, write) and provides additional local caching. It translates remote calls to the AEM Assets server to optimized AEM HTTP requests. The following diagram depicts the AEM desktop app architecture.

![AEM desktop app architecture](assets/arch_v1.png)

*Figure: desktop app architecture*

When a file is saved, the extra caching on write ensures it is stored locally first, allowing the user to avoid waiting for the network transfer. Then, after a predefined delay (30s) the file is uploaded to AEM in the background, and then asset is uploaded to AEM. AEM desktop app provides a UI for monitoring the status of background file uploads.

## Recommended use of AEM desktop app {#recommended-use-of-aem-desktop-app}

Key capabilities of the AEM desktop app include:

* **Opening files from AEM Assets Web UI on desktop**. From the Web UI, you can reveal assets on desktop (in Finder, Explorer), or open an asset using a desktop application.

* **Check out and check in**. Assets can be checked out for editing, they are marked as locked for the user in AEM Assets. After editing, the asset can be checked in to unlock it.

* **Save changes to files**. Any change that you save to the file in the network share is uploaded to AEM automatically, and a new version is created.

* **Place linked assets in other documents**. In applications, such as Creative Cloud ([!DNL Adobe Photoshop], [!DNL Adobe InDesign], and [!DNL Adobe Illustrator]), you can place an external file as a link. For example, you can place an image into an InDesign document. In this case, the network share mount lets you browse and select assets from AEM for placement. Placing linked files also works in some non-Adobe apps, such as MS&reg; Office.

* **Reference resolution in AEM**. If both the placed files and the main files with link are stored in AEM, it can automatically provide server-side information about the asset references.

* **Access the asset from the desktop**. In the mounted network share, a contextual menu provides a [!UICONTROL More Info] dialog box (larger preview, key metadata) and the ability to open an asset in the AEM UI.

* **Uploading large, hierarchical folders in bulk**. If you use the **Create** > **Folder Upload** option in AEM UI to upload assets, the AEM desktop app uploads the selected folder hierarchy to AEM in the background. Upload progress is monitored with a dedicated UI in the desktop app.

## Inappropriate use of AEM desktop app {#inappropriate-use-of-aem-desktop-app}

* Do not use the AEM desktop app to manage assets from the desktop. AEM desktop app was not built as a replacement for network drives. Use the following capabilities instead:

  * AEM Assets Web UI for digital asset management (finding or sharing assets, metadata, and copy or move).

  * AEM desktop app [!UICONTROL Folder Upload] to upload large, hierarchical folders.

* Do not treat AEM desktop app as a "desktop sync" client for AEM Assets. The key benefit of AEM desktop app here is that it provides "virtual" access to the whole repository, and desktop sync applications typically synchronize just assets belonging to one user. AEM desktop app provides some level of caching and background upload; still, it works very differently from typical "Sync" applications, such as Adobe Creative Cloud desktop app or Microsoft OneDrive.

* Do not use AEM desktop app network drives to save assets frequently. All save operations are transmitted to AEM Assets. Therefore, it is impractical to perform intensive edit operations directly in the mounted AEM Assets repository. Editing an asset directly in the mounted repository crams the asset's timeline with irrelevant versions and imposes additional overheads on the server.

* Do not use AEM desktop app for migration of large amounts of data from one AEM instance to another. See the [Migration Guide](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/administer/assets-migration-guide) to plan and execute asset migrations. In contrast, the desktop app [supports bulk uploading](use-app-v1.md#bulkupload) large number of assets for the first time in [!DNL Adobe Experience Manager].

## Recommendations for selected use cases {#recommendations-for-selected-use-cases}

### Access to assets for creative users {#access-to-assets-for-creative-users}

AEM desktop app provides virtual access to the whole DAM repository - and it might be complicated for the creative users on desktop to find and access the right assets on their desktop. Use these best practices to simplify that for them.

* Use collaboration features in AEM Assets Web UI to provide more direct access to the right assets for the creative user. Sharing folders or collections, providing Smart Collections (saved searches), or sending notifications with pointers to the right assets are some of them. Creative user can then use desktop actions in the Web UI for quick access to these assets on their desktop.

* Consider the right permissions for assets (access control) to simplify the view into the DAM repository for the creative users, basically limiting their access to only assets they need or are interested in:

  * Certain areas not relevant to the creative users might be denied for their user groups, to remove them from their view, also on desktop.

  * Most assets in DAM are final and not intended for changing - such assets should be read-only for the creative users.

  * Only assets that require changes or retouching should be write-enabled for the creative users. Some organizations use AEM Projects and the folders that they create to host assets that are still subject to changes.

### Searching assets {#searching-assets}

To search for a file that you want to open on the desktop:

* Use the AEM Assets Web UI to locate the asset. Not only is search in AEM Assets powerful (search facets, saved searches), it also provides additional capabilities to find the right asset. These include additional filters, like the ability to search assets based on status (approval, expiry), collections, tasks, notifications, and sharing folders / collections with other users / groups.

* After you locate the asset, use desktop actions in AEM UI to access the asset on the desktop.

### Updating assets opened using AEM desktop app {#updating-assets-opened-using-aem-desktop-app}

If you edit an asset directly at the location mapped from AEM Assets to a local network share, the asset is uploaded to AEM each time you save it on desktop. In addition, AEM creates a version and generates renditions.

If an asset stored in AEM needs an update:

* For **minor updates**, such as minor retouching requests in the approval process:

  * Check out the file and open it on the desktop.

  * Update the file.

  * Save the updated version. The asset is updated, and the timeline displays the original version for comparison.

* For **major updates**, such as a change request that requires a small creative WIP cycle:

  * Use the Reveal option to open the appropriate folder on the desktop.

  * Copy the file to a WIP folder outside of the mapped AEM Assets share (for example, copy the file into a folder synced with Adobe Creative Cloud desktop app).

  * Work on the file and save it intermittently. The changes are not saved to AEM Assets.

  * After the edits are complete, move, copy, or save the file mapped from AEM to upload it as a new version.

## Network performance {#network-performance}

A good user experience with the AEM desktop app relies on stable network connectivity and a well-tuned server, particularly for uploading and updating assets. These recommendations are for the network / IT teams in organizations.

### Network considerations {#network-considerations}

To understand best practices around AEM Assets network configuration, go to [How to bulk migrate assets](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/administer/assets-migration-guide) document. Some of the important aspects that help optimize the AEM desktop app experience for the users include:

* **Use a properly configured Dispatcher**. Use the AEM Dispatcher for additional security and ensure that it is configured for [AEM desktop app connection to AEM behind a Dispatcher](install-configure-app-v1.md#connect-to-an-aem-instance-behind-a-dispatcher)

* **Save bandwidth**. Consider turning off icon preview in Finder on Mac when browsing the mounted repository using Finder. The Finder requests each file to generate a preview and causes the desktop app to download and cache the asset locally. While saving bandwidth, it also decreases user experience for the users on the desktop, so it should be done when working on repositories with large assets or limited bandwidth.

>[!NOTE]
>
>To turn off icon previews, in the Finder go to [!UICONTROL View], select [!UICONTROL View Options], and then un-check the [!UICONTROL Show icon preview] option. This only works for the current folder - to make it a default, click the [!UICONTROL Use as default] option in the same dialog.

### Optimizing server performance {#optimizing-server-performance}

To understand how AEM Assets server should be optimized for performance, go to [AEM Assets Performance Tuning Guide](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/administer/performance-tuning-guidelines). Some of the important aspects of the server performance for AEM desktop app are around optimizing workflow configuration so that it performs well for asset uploads:

* **More performant asset upload**. Configure the [AEM Asset Update workflow model to be transient](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/administer/performance-tuning-guidelines).

* **Limit server CPU for uploads**. Ensure that the maximum parallel workflow jobs parameter is set correctly, so that uploads do not exhaust all the CPU.
