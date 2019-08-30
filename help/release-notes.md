---
title: AEM desktop app Release Notes
seo-title: AEM desktop app Release Notes
description: Release details, enhancements, new features, compatibility, and download links for AEM desktop app v1.x.
seo-description: Release details, enhancements, new features, compatibility, and download links for AEM desktop app v1.x.
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

# AEM desktop app Release Notes {#release-notes-v2}

| Products      |  Adobe Experience Manager (AEM) desktop app                        |
|---------------|--------------------------------------------------------------------|
| App version   | 2.0 (2.0.0.4)                                                 |
| AEM version supported | AEM 6.5, AEM 6.4, AEM 6.3 (with compatibility package)     |
| Type          | Major release                                                      |
| Release date  | August 31, 2019                                                    |
| Download URLs |  [Mac OS X 64-bit](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-osx-2.0.0.4.dmg); Windows 32-bit (coming soon); Windows 64-bit (coming soon)  |

## System requirements and prerequisites {#system-requirements-and-prerequisites-v2}

AEM desktop app is compatible with the following operating systems:

* Mac OS X 10.10 or later, with latest bug fixes.
* Windows 7 and Windows 10 with the latest service packs and bug fixes.

The app works with the following AEM versions, whether deployed on-premise or on Adobe Managed Services (AMS):

* [AEM 6.5.0](https://helpx.adobe.com/experience-manager/6-5/release-notes.html) or later
* [AEM 6.4.4](https://helpx.adobe.com/experience-manager/6-4/release-notes/sp-release-notes.html) or later
* AEM 6.4.0 - 6.4.3 with [compatibility package](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support)
* AEM 6.3.3.1 and later with [compatibility package](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support)
* For AEM 6.3, no [service packs are planned](https://helpx.adobe.com/experience-manager/maintenance-releases-roadmap.html). Adobe recommends to upgrade to a later AEM version.

The version of the app you plan to install on your local machine requires a specific Adobe Experience Manager server version/additional server-side components (service packs, hot fixes, or feature packs). Contact your AEM administrator for help.

### Support for different asset and file types {#support-for-file-types}

The application supports assets stored in AEM that represent binary file for its basic operations. Opening files in the native desktop application relies on the operating system association of the specific file types like PNG or JPG to specific applications like Mac Preview or Adobe Photoshop.

A few file types support placing linked assets in the binary. The application pre-downloads the linked assets if the asset is present in the AEM repository when such binary files are opened using the desktop app. Currently supported file types are:

* Adobe InDesign files (INDD format)
* Adobe Illustrator files (AI format)
* Adobe Photoshop files (PS format)

The feature is supported with Adobe Creative Cloud 2018 and Creative Cloud 2019 versions of the above application. The app uses a heuristic, best-match approach to map the local desktop paths of linked assets to URLs on the AEM server. It relies on a few assumptions:

* Paths to placed files in the native application use a global desktop path (placed from the local network share shown with “Reveal” option)
* Paths are stored in the file’s XMP record by the native app
* AEM has extracted the XMP record with the paths to the asset’s metadata record
* The paths can be matched to assets in AEM (meaning, the placed files are also in AEM under a matching path)

## New features and enhancements {#whats-new-added}

To know the details, see [What's New in the App](introduction.md#whats-new-v2).

## Installation instructions {#installation-instructions-v2}

To know how to install and configure the app, see [Install AEM desktop app](install-upgrade.md).

If you are upgrading from a previous AEM desktop app, you must follow these best practices for transitioning that are listed at [upgrade from previous version](install-upgrade.md#upgrade-from-previous-version).

## Important notes about how the app works {#how-app-works}

It is important to understand the following about the application and how it works.

* The application provides full control over operations that require full transfer of asset binaries from and to AEM (open, edit, upload changes, and upload assets).
  * If you want to work with the asset on desktop, you need to explicitly Open, Edit, or Download to your desktop, either individually, in a folder, or via multi-selection.
  * If you want to get local changes to assets uploaded to AEM, you need to select [!UICONTROL Upload Changes], either individually or via multi-selection.
  * The application is not a 'sync client' that synchronizes assets across the desktop and AEM.
  * The application does not provide a network share that maps the AEM repository as a virtual folder structure.
* The list of assets shown by the application is based on the status of the AEM Assets repository. Any files downloaded locally and then renamed in the local files or cache folder are not displayed or managed by the application.
* If the app does not display the expected results, click refresh icon in the top bar.
* The local network share, shown when you use [!UICONTROL Reveal File] action, only shows files (and folders) that are available locally. [!UICONTROL Reveal File] and [!UICONTROL Reveal Folder] pre-downloads assets to help get the right assets showing in the local network share.
* SMB/WebDAV is used when an Adobe Creative Cloud app reads the asset files linked/placed in a native file of the Creative Cloud app.

## Known issues {#known-issues-v2}

* At times, the interface of the desktop app gets blank. Right-click and click [!UICONTROL Refresh] to load the application again. Such a refresh resets the state of the app and you start at the welcome screen at the root of the DAM repository.
* Infrequently, the progress bar does not display correctly when the uploading asset changes.
* At times, on Windows, an asset's status may immediately change to [!UICONTROL Edited Locally] after opening it, even though you may not have edited it. Click [!UICONTROL Refresh] to update.
* After applying and removing the filter to find all locally edited assets, the app does not take users to their search results or folder view that the users started with. The app displays the root folder of the DAM repository.
* At times, when you connect to a URL that doesn’t have AEM server running, the connect screen becomes unresponsive. Exit the application and start it again.
* When uploading changes to an asset with comments, the comments are stored with the asset in AEM but are not visible as versioning comments.

>[!MORELIKETHIS]
>
>* [AEM documentation](https://helpx.adobe.com/support/experience-manager/6-5.html)
>* [Use AEM desktop app](using.md)
>* [Install and upgrade desktop app](install-upgrade.md)
>* [Best pracitces, troubleshooting tips](troubleshoot.md)