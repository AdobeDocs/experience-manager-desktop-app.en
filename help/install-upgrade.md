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

# Install AEM desktop app{#install-app-v2}

Install and configure AEM desktop app to work with AEM Assets servers and map the assets to mount as a drive on your desktop.

To use AEM desktop app,

* Download and install the application. Upgrade if you are already using v1.x.
* Ensure that your AEM server version is supported by AEM desktop app. See the compatibility matrix in release notes.
* Test the connection using a few assets.

## System requirements {#tech-specs-v2}

For detailed information, see the [AEM desktop app release notes](release-notes.md).

## Install app {#install-app-v2}

Only one instance of the AEM desktop app can be installed and be active at a time.

## Upgrade from previous version {#upgrade-from-previous-version-v2}

Adobe strongly recommends that you use the latest version of the desktop app. Upgrade using the following instructions, if you are using v1.x.

1. Before upgrading, sync all your assets. Upload your changes, else you will lose the changes during upgrade.

1. Uninstall the previous version of the app.

1. Remove cache and logs of app v1.x if you do not need these. If in doubt, leave the cache and logs intact.

1. Install the latest version of the application.

## Proxy support {#proxy-support-v2}

AEM desktop app uses system's pre-defined proxy to connect to the Internet over HTTPS. The app can only connect using a network proxy that does not require extra authentication.

If you configure or modify proxy server settings for Windows (Internet Options &gt; LAN Settings), restart the AEM desktop app for the changes to take effect.

If your proxy requires authentication, the IT team can whitelist the AEM Assets URL in the proxy server settings to allow the application traffic to pass through.

>[!NOTE]
>
>AEM desktop app can handle assets up to 40 GB.

## Additional resources {#additional-resources-v2}

* [Introduction to AEM desktop app](https://helpx.adobe.com/experience-manager/kt/eseminars/ccoo-aem-desktop-app.html)
* [Use AEM desktop app](use-app-v1.md)  

* [Understand Check-in/Check-out with AEM desktop app](https://helpx.adobe.com/experience-manager/kt/assets/using/checkin-checkout-technical-video-understand.html)
* [Using desktop app with AEM Assets](https://helpx.adobe.com/experience-manager/kt/assets/using/checkin-checkout-technical-video-understand.html)
* [Troubleshooting AEM desktop app](troubleshoot-app-v1.md)