---
title: Install and configure desktop app v1.10
description: Install and configure [!DNL Experience Manager] desktop app version 1.10 to work with [!DNL Assets] servers and map the assets to mount as a drive on your desktop.
exl-id: 7f3bdfb1-d345-4e48-b020-6e06531f46f2
---
# Install and configure [!DNL Experience Manager] desktop app v1.10 {#install-and-configure-aem-desktop-app}

Using the [!DNL Experience Manager] desktop app, the assets within [!DNL Experience Manager] are easily accessible on your local desktop and can be used in any desktop applications. Assets can be revealed in Mac Finder or Windows Explorer, edited in desktop apps, and changes are saved back to [!DNL Experience Manager], creating a new version upon upload.

This integration enables different roles to manage assets centrally within the organization in Assets, access them in Creative Cloud and other applications, and easily comply with various standards, including branding.

To use the [!DNL Experience Manager] desktop app,

* Make sure that your [!DNL Experience Manager] server version is compatible with the [!DNL Experience Manager] desktop app. See the [compatibility matrix](release-notes-of-v1.md#compatibilitymatrix).

* Download and install the application.

* Test the connection using a few assets. See [Access and open assets on your desktop](use-app-v1.md#openondesktop).

## System requirements, prerequisites, and download links {#system-requirements-prerequisites-and-download-links}

For detailed information, see the [[!DNL Experience Manager] desktop app release notes](release-notes-of-v1.md).

## Install and connect the app to [!DNL Experience Manager] server {#install-and-connect-aem-desktop-app-to-aem-server}

For details, see [Install and connect [!DNL Experience Manager] desktop app to [!DNL Experience Manager] server](use-app-v1.md#installandconnect).

>[!NOTE]
>
>Only one instance of the [!DNL Experience Manager] desktop app can be installed and be active at a time.

## File handling {#file-handling}

When changing a file from a network share location mounted by the desktop app, files are saved to that location in two phases. In the first phase, a file is saved locally. A user can save the file and continue working on the file, without waiting for the transfer to complete.

In the second phase, the desktop app uploads the updated file to the [!DNL Experience Manager] server after a predefined delay (for example, 30s). This operation occurs in the background. Use the View Asset Status option to view the status of the upload operation.

1. Upload an asset to Assets.

1. Click the [!DNL Experience Manager] desktop app icon from the toolbar.

1. From the menu, select the View Asset Status option.

1. From the dialog, review the status of the upload operation.

>[!NOTE]
>
>[!DNL Experience Manager] desktop app can handle assets up to 40 GB in size.

## Connect to an [!DNL Experience Manager] instance behind a Dispatcher {#connect-to-an-aem-instance-behind-a-dispatcher}

The copy and move methods in the Assets API require the following additional headers to be passed to [!DNL Experience Manager]:

* X-Destination
* X-Depth
* X-Overwrite

[!DNL Experience Manager] desktop connects to [!DNL Experience Manager] using a URL that includes the default port. Therefore, the `virtualhosts` setting in the Dispatcher configuration should include the default port number. For more information around `virtualhosts` configuration, see [identify virtual hosts](https://experienceleague.adobe.com/en/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration#identifying-virtual-hosts-virtualhosts).

For additional information on configuring the Dispatcher to pass through these additional headers, see [Specifying the HTTP Headers](https://experienceleague.adobe.com/en/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration#specifying-the-http-headers-to-pass-through-clientheaders).

### Proxy support {#proxy-support}

The [!DNL Experience Manager] desktop app uses the system's pre-defined proxy to connect to the Internet over HTTPS. The app can only connect using a network proxy that does not require extra authentication.

If you configure or modify proxy server settings for Windows (Internet Options &gt; LAN Settings), restart the [!DNL Experience Manager] desktop app for the changes to take effect.

>[!NOTE]
>
>Proxy configuration is only applied when you start the desktop app. Close and re-launch the app for any changes to take effect.

If your proxy requires authentication, the IT team can allow the Experience Manager Assets URL in the proxy server settings to allow the application traffic to pass through.

## Customize the Asset Info dialog {#customize-the-asset-info-dialog}

You can customize the Asset Info dialog by overlaying one or both of these components:

* The Granite user interface page at `/libs/dam/gui/content/assets/moreinfo`.

* The HTL `/css/javascript` component at `/libs/dam/gui/components/admin/moreinfo`.

Which component is overlaid depends on the nature of the customization. To change which components are displayed as part of the Asset Info dialog, overlay the Granite user interface page. To change the HTML, CSS, or JavaScript content of the dialog, overlay the HTL component.

## Manage cache {#manage-cache}

On Windows, the cache is at `%LOCALAPPDATA%\Adobe\AssetsCompanion\Cache\`, where is an encoded version of the [!DNL Experience Manager] host configured in the desktop app. For example, `http://localhost:4502` appears as `http%3A%2F%2Flocalhost%3A4502%2F`.

On macOS X, a similar directory is at `~/Library/Group Containers/group.com.adobe.aem.desktop/cache`.

### In-app option to manage cache {#in-app-option-to-manage-cache}

You can control the amount of disk space made available for local caching purposes. The artifacts from the Assets server are cached locally for a smoother experience. You can change the defaults to suit your requirements. Also, you can clear the cache to fetch all assets afresh. To set the desired options, click the application's icon and click **[!UICONTROL Advanced]** > **[!UICONTROL Manage Cache]**. ****

>[!NOTE]
>
>When you clear the cache, it preserves your unsaved changes. Any assets not checked into the [!DNL Experience Manager] server are retained and not deleted.

### Change location of cache on Windows {#change-location-of-cache-on-windows}

The default location of the cache for the [!DNL Experience Manager] desktop app is as follows:

* In Windows, `%LocalAppData%\Adobe\AssetsCompanion\Cache\EncodedAEMEndpoint`.

* In Mac, `~/Library/Group/Containers/group.com.adobe.aem.desktop/cache/EncodedAEMEndpoint`.

The `EncodedAEMEndpoint` is the app's configured [!DNL Experience Manager] endpoint URL. The value is an encoded version of the targeting URL of the [!DNL Experience Manager] server. For example, if the application is targeting `http://localhost:4502`, the directory name is `http%3A%2F%2Flocalhost%3A4502`. The Windows path to the cache directory in this example is `%LocalAppData%\Adobe\AssetsCompanion\Cache\http%3A%2F%2Flocalhost%3A4502`.

To point the application to a different folder or a different drive, edit the application's configuration file.

1. Navigate to the app's installation directory. The default location on Windows is `C:\Program Files (x86)\Adobe\Adobe Experience Manager Desktop`.

1. Edit the `Adobe Experience Manager Desktop.exe.config` file with a text editor.

   Administrator privileges are required to save changes to this file.

1. Search for the string "ProxyCacheRoot." You see that its value is set to the cache location `%LocalAppData%\Adobe\AssetsCompanion\Cache`. Simply change this value to any valid path.

   >[!NOTE]
   >
   >The app automatically creates an *&lt;Encoded AEM Endpoint&gt;* subdirectory. This behavior is not configurable.

>[!MORELIKETHIS]
>
>* Watch an [Introduction to [!DNL Experience Manager] desktop app](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/creative-workflows/aem-desktop-app) (5 minutes, 43 seconds).
>* [Use [!DNL Experience Manager] desktop app](use-app-v1.md).
>* [Troubleshooting [!DNL Experience Manager] desktop app](troubleshoot-app-v1.md).
