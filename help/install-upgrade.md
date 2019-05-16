---
title: Install and configure AEM desktop app
seo-title: Install and configure AEM desktop app
description: Install and configure AEM desktop app to work with AEM Assets servers and map the assets to mount as a drive on your desktop.
seo-description: Install and configure AEM desktop app to work with AEM Assets servers and map the assets to mount as a drive on your desktop.
uuid: 79bc9de9-5708-41f9-ac43-68c1fd2a2129
contentOwner: asgupta
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: installing
topic-tags: aem-desktop-app
products: SG_EXPERIENCEMANAGER/6.3
products: SG_EXPERIENCEMANAGER/6.2
products: SG_EXPERIENCEMANAGER/6.1
discoiquuid: f6365302-1690-4719-9b8c-035719422740
index: y
internal: n
snippet: y
---

# Install AEM desktop app {#install-app-v2}

## System requirements {#tech-specs-v2}

For detailed information, see the [AEM desktop app release notes](release-notes.md).

## Upgrade from app v1.x to app v2 {#upgrade-from-previous-version}

If you are an existing user of the app v1.x, then understand the differences and similarities between both versions. Also, follow the below guidelines, to transition from desktop app v1.x to v2.0.

To upgrade from v1.x to v2.x of the app, follow these instructions:

1. Before upgrading, sync all your assets. Upload all the changes using app v1.x. This is to avoid losing any changes when uninstalling the app v1.x.
1. Uninstall app v1.x. When uninstalling v1.x, clear the cache.
1. Reboot your machine.
1. Download and install the latest app. Follow the instructions below.

## Install {#install-v2}

To install the desktop app, follow these steps. Uninstall any existing Adobe Experience Manager desktop app v1.x before installing v2.0 pre-release build. For more info, see above.

1. Keep the URL and credentials of your AEM deployment handy.
1. Ensure that your setup meets the compatibility requirements mentioned in the release notes. Download the applicable [compatibility package](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support) and install it using the AEM Package Manager. To install a package, see [How to work with Packages](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/package-manager.html). Skip this step if you are using AEM 6.4.4/AEM 6.5.0 or later.
1. Execute the installer binary and follow the on-screen instructions to install.
1. Restart the machine as prompted. Launch the desktop app to configure.
1. To connect the app with an AEM repository, click on the app icon in the tray to launch the app. Provide the address of the AEM instance. Click Connect and provide the credentials.

![Connection screen of desktop app to input server address](assets/connect_da2.png "Connection screen to input server address")

>[!Caution]
>
>Ensure there are not leading or trailing spaces before the address of the your AEM server. Otherwise you cannot connect to the AEM server.

1. Upon successful connection, you can view the list of folders and assets available in the root folder of the AEM DAM. You can browse the folders from within the app.

![Upon login the app displays the DAM contents](assets/firstview_da2.png "Upon login the app displays the DAM contents")

## Set preferences {#set-preferences}

To change preferences, click ![More options icon](assets/do-not-localize/more_options_da2.png) and Preference ![Preferences icon](preferences_da2.png). In the Preferences window, adjust the values of the following:

* Launch application on login.
* Show window when application starts.
* **Cache Directory**: Location of local cache of the app (it contains the locally downloaded assets).
* **Network Drive Letter**: The drive letter used to locally mount AEM Assets DAM. Do not change this if you are not sure. You may stop seeing the placed assets.
* **Maximum Cache Size**: Allowed cache on hard disk in GB that is used towards storing locally downloaded assets.
* **Current cache size**: Amount of assets downloaded locally.
* **Automatically download linked assets**: The assets that are placed in the supported native Creative Cloud apps are fetched automatically if you download the original file.
* **Maximum number of downloads**: When downloading assets for the first time (via Reveal, Open, Edit, Download, or similar option), the assets are downloaded only if the batch contains less than this number. Default value is 50. Do not change if you are unsure. Increasing the value may lead to longer wait times and decreasing the value may not allow you to download required assets or folders in one go.