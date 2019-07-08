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

| Products      |  Adobe Experience Manager (AEM) desktop app                                                                                                                                                                                                            |
|---------------|--------------------------------------------------------------------|
| Version       | 2.0                                                                                                                                                                                                                     |
| Type          | Major release                                                                                                                                                                                                                                          |
| Date          | May 2019                                                                                                                                                                                                                                        |
| Download URLs |  [Mac OS X 64 bit](https://example.com); [Windows 32 bit](https://example.com); [Windows 64 bit](https://example.com) |

## Compatibility {#compatibility-v2}

The app works with the following AEM versions, whether deployed on-premise or on Adobe Managed Services (AMS):

* [AEM 6.5.0](https://helpx.adobe.com/experience-manager/6-5/release-notes.html) or later
* [AEM 6.4.4](https://helpx.adobe.com/experience-manager/6-4/release-notes/sp-release-notes.html) or later
* AEM 6.4.0 - 6.4.3 with [compatibility package](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support)
* AEM 6.3.3.1 and later with [compatibility package](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support)

For AEM 6.3, no [service packs are planned])(https://helpx.adobe.com/experience-manager/maintenance-releases-roadmap.html). Adobe Experience Manager desktop app v2.x releases might not support all new features for AEM 6.3 deployments. It is highly recommended to update to a later AEM version.

## System requirements and prerequisites {#system-requirements-and-prerequisites-v2}

AEM Desktop is compatible with the following operating systems:

* Mac OS X 10.10 or later, with latest bug fixes.
* Windows 7 and Windows 10 with the latest service packs and bug fixes.

The version of the app you are planning to install on your local machine requires a specific Adobe Experience Manager server version/additional server-side components (service packs, hot fixes or feature packs). Ensure that the AEM server is properly configured before you connect to it for the first time. If you require help, contact your AEM administrator. See the compatibility matrix for the supported versions.

| Version | Revision               | Release Date | Compatibility                                               |
|---------|------------------------|--------------|-------------------------------------------------------------|
| 2.0    | Build numbers (Mac and Win) | May 2019 | Supported AEM versions |

### Support for different asset and file types {#support-for-file-types}

The application supports assets stored in AEM that represent binary file for its basic operations. Opening files in the native desktop application relies on the operating system association of the specific file types like PNG or JPG to specific applications like Mac Preview or Adobe Photoshop.

A few file types support placing linked assets in the binary. The application pre-downloads the linked assets if the asset is present in the AEM repository when such binary files are opened using the desktop app. Currently supported file types are:

* Adobe InDesign files (INDD)
* Adobe Illustrator files (AI)
* Adobe Photoshop files (PS)

The feature is supported with Adobe Creative Cloud 2018 and Creative Cloud 2019 versions of the above application. The app uses a heuristic, best-match approach to map the local desktop paths of linked assets to URLs on the AEM server. It relies on a few assumptions:

* Paths to placed files in the native application use a global desktop path (placed from the local network share shown with “Reveal” option)
* Paths are stored in the file’s XMP record by the native app
* AEM has extracted the XMP record with the paths to the asset’s metadata record
* The paths can be matched to assets in AEM (meaning, the placed files are also in AEM under a matching path)

## What are the new features and enhancements added {#whats-new-added}

To know the details, see [What's New in the App](introduction.md#whats-new-v2).

## Installation instructions {#installation-instructions-v2}

To know how to install and configure the app, see [Install AEM desktop app](install-upgrade.md).

If you are upgrading from a previous AEM desktop app, you must follow these best practices for transitioning that are listed at [upgrade from previous version](install-upgrade.md#upgrade-from-previous-version).

## Important notes about how the app works {#how-app-works}

It is important to understand the following about the application and how it works.

* The application provides full control over operations that require full transfer of asset binaries from and to AEM (open, edit, upload changes, upload)
  * If you want to work with the asset on desktop, you need to explicitly Open, Edit, or Download to your desktop, either individually, in a folder, or via multi-selection
  * If you want to get local changes to assets uploaded to AEM, you need to select Upload Changes, either individually or via multi-selection
  * The application is not a “sync client” that synchronizes assets across the desktop and AEM
  * The application does not provide a network share that maps the AEM repository as a virtual folder structure
* The list of assets shown by the application is based on the status of the AEM Assets repository.
  * Any files downloaded locally and then renamed in the local files or cache folder are not displayed or managed by the application.
* Manually refresh the display after asset upload or some operations. The display does not always update automatically
* The local network share, shown when you use “Reveal” action, only shows files (and folders) that are available locally. Reveal and Reveal folder pre-downloads assets to help get the right assets showing in the local network share.

## Known issues {#known-issues-v2}

* Sometimes, the UI of the desktop app gets blank. Use the right-click and “reload” to enforce loading the embedded application again. Note it would reset the state of the app and get you to the main screen
* Infrequently, the progress bar does not display correctly when the uploading asset changes.
* At times, on Windows, an asset's status may immediately change to ‘Edited Locally’ after opening it, even though you may not have edited it.
* After you click the Refresh button, the controls to page and sort assets are reset.
* After applying and removing the filter to find all locally edited assets, the app does not take users to their search results or folder view that the users started with.
* If you Upload Changes in the Locally Edited view, the status of the files does not refresh automatically (use Refresh button)
* Sometimes, when you connect to a URL that doesn’t have AEM server running, the connect screen can get stuck. Exit the application and start it again.
* When uploading changes to an asset with a comment, the comment will be stored with the asset in AEM but will not be visible as a versioning comment until the next action of uploading changes. This is a result of the AEM versioning model and should be improved to show the latest comment in future releases of AEM service packs.

## Helpful resources {#helpful-resources-v2}

* [AEM documentation](https://helpx.adobe.com/support/experience-manager/6-5.html)
* [Use AEM desktop app](using.md)
