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

# AEM desktop app Release Notes {#aem-desktop-app-release-notes-v2}

## Release information {#release-information-v2}

| Products      |  Adobe Experience Manager (AEM) desktop app                                                                                                                                                                                                            |
|---------------|--------------------------------------------------------------------|
| Version       | 2.0                                                                                                                                                                                                                     |
| Type          | Major release                                                                                                                                                                                                                                          |
| Date          | May 2019                                                                                                                                                                                                                                        |
| Download URLs |  [Mac OS X 64 bit](https://example.com); [Windows 32 bit](https://example.com); [Windows 64 bit](https://example.com) |
| Compatibility | List of AEM versions |

## System requirements and prerequisites {#system-requirements-and-prerequisites-v2}

AEM Desktop is compatible with the following operating systems:

* Mac OS X 10.10 or later, with latest bug fixes.
* Windows 7 and Windows 10 with the latest service packs and bug fixes.

The version of AEM Destkop App you are planning to install on your local machine requires a specific AEM server version/additional server-side components (service packs, hot fixes or feature packs). Ensure that the AEM server is properly configured before you connect to it for the first time. If you require help, contact your AEM administrator. See the compatibility matrix for the supported versions.

| Version | Revision               | Release Date | Compatibility                                               |
|---------|------------------------|--------------|-------------------------------------------------------------|
| 2.0    | Build numbers (Mac and Win) | May 2019 | Supported AEM versions |

## Installation instructions {#installation-instructions-v2}

For detailed instructions, see [Install AEM desktop app](using.md).

## Known issues {#known-issues-v2}

* Infrequently, the progress bar does not display correctly when the uploading asset changes.
* At times, on Windows, an asset's status may immediately change to ‘Edited Locally’ after opening it, even though you may not have edited it.
* After you click the Refresh button, the controls to page and sort assets are reset.
* After you upload the changes to an asset, the edit or check-out flag is not removed as expected.

## Limitations {#limitations-v2}

* You cannot undo or revert the changes made to an asset by editing it locally.
* The list of assets shown by the application is based on the status of the AEM Assets repository. Any files downloaded locally and then renamed in the local files or cache folder are not displayed or managed by the application.
* You cannot select multiple folders in the pre-release build.
* AEM desktop app is not a ‘sync client’ that synchronizes assets across your desktop and AEM.
* Manually refresh the display after asset upload or some operations. The display does not update automatically.

## Helpful resources {#helpful-resources-v2}

* [AEM Documentation](https://helpx.adobe.com/support/experience-manager/6-4.html)
* [Use AEM desktop app v1.x](use-app-v1.md)
* [AEM desktop app v1.x best practices](best-practices-for-v1.md)