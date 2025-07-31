---
title: Best practices for and troubleshooting [!DNL Adobe Experience Manager] desktop app
description: Follow best practices and troubleshoot to resolve the occasional issues related to installation, upgrade, configuration, and so on.
exl-id: f388e4ac-907d-4093-ba6f-86ecdafeb015
---
# Troubleshoot [!DNL Adobe Experience Manager] desktop app {#troubleshoot-v2}

[!DNL Adobe Experience Manager] desktop app connects to an [!DNL Experience Manager] deployment's Digital Asset Management (DAM) repository. The app fetches repository information and search results on your machine, downloads and uploads files and folders, and includes capabilities to manage conflicts with the Assets user interface.

Read on to troubleshoot the app, learn the best practices, and find out the limitations.

## Best practices {#best-practices-to-prevent-troubles}

Adhere to the following best practices to prevent some common issues and troubleshooting.

* **Understand how the desktop app works**: Before starting to use the application, spend a few moments knowing how the app works. Know about linking between the [!DNL Experience Manager] web interface and the desktop, repository mapping, asset caching, saving locally and uploading in the background. See [how it works](release-notes.md#how-app-works).

* **Avoid unsupported characters in folder names**: Do not use whitespaces and invalid characters when creating or uploading folders. See a list of characters at [Create folders in [!DNL Adobe Experience Manager Assets]](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/managing/manage-assets#creating-folders). Unsupported characters in the folder name may impact some [!DNL Experience Manager] use cases.

* **Best practices to avoid conflicts**: To avoid potential conflicts when collaborating on multiple assets, go to [avoid editing conflicts](using-desktop-app.md#adv-workflow-collaborate-avoid-conflicts).

* **Use folder upload for large, hierarchical folders**: Instead of using the Assets web interface or other methods, use the [!DNL Experience Manager] desktop app to upload large folders. The app uploads the assets in the background with logging and monitoring. See [bulk upload assets](using-desktop-app.md#bulk-upload-assets).

* **Use the latest version**: Use the latest app version. Always check for compatibility before installing either a new app version or before upgrading to a newer [!DNL Experience Manager] version. See [release notes](release-notes.md).

* **Use the same drive letter**: Use the same drive letter across an organization to map to the [!DNL Experience Manager] DAM. To see assets placed by other users, the paths must be the same. Using the same drive letter ensures a constant path to DAM assets. The assets remain placed and are not removed even if different drive letters are used by different users.

* **Mind the network**: Network performance is critical to [!DNL Experience Manager] desktop app's performance. If you face a slowed response to file transfers or bulk operations, turn off the features or apps that might cause lots of network traffic.

* **Unsupported use cases for desktop app**: Avoid using the app for asset migration, as it requires planning and additional tools. It is also not suitable for heavy-duty DAM operations, such as moving large folders, large uploads, or advanced metadata searches. Additionally, do not use it as a sync client, as its design principles and usage patterns differ from sync clients like Microsoft OneDrive or Adobe Creative Cloud desktop sync.

* **Time out**: Currently, the desktop app does not have a configurable timeout value that disconnects the connection between [!DNL Experience Manager] server and desktop app after a fixed time interval. When uploading large assets, if the connection gets timeout after a while, the app retries to upload the asset a few times by increasing the upload timeout. There is no recommended way to change the default timeout settings.

## How to troubleshoot {#troubleshooting-prep}

To troubleshoot desktop app issues, be aware of the following information. Also, it prepares you to convey the issues better to Adobe Customer Support if you choose to seek support.

### Location of log files {#check-log-files-v2}

The [!DNL Experience Manager] desktop app stores its log files in the following locations depending on the operating system:

On Windows: `%LocalAppData%\Adobe\AssetsCompanion\Logs`

On Mac: `~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`

When uploading many assets, if some files fail to upload, see `backend.log` file to identify the failed uploads.

>[!NOTE]
>
>When working with Adobe Customer Support on a support request or ticket, you can be asked to share the log files to help the Customer Support team understand the issue. Archive the entire `Logs` folder and share it with your Customer Support contact.

### Change level of details in log files {#level-of-details-in-log}

To change the level of details in log files:

1. Ensure that the application is not running.

1. On Windows system:

    1. Open a command window.

    1. Launch the [!DNL Adobe Experience Manager] desktop app by running the command:

    ```shell
    set AEM_DESKTOP_LOG_LEVEL=DEBUG&"C:\Program Files\Adobe\Adobe Experience Manager Desktop.exe
    ```

    On Mac system:

    1. Open a terminal window.

    1. Launch the [!DNL Adobe Experience Manager] desktop app by running the command:

    ```shell
    AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app
    ```

The valid log levels are DEBUG, INFO, WARN, or ERROR. The verbosity of the logs is highest in DEBUG and lowest in ERROR.

### Enable debug mode {#enable-debug-mode}

To troubleshoot, you can enable the debug mode and get more information in the logs.

>[!NOTE]
>
>Valid log levels are DEBUG, INFO, WARN, or ERROR. The verbosity of the logs is highest in DEBUG and lowest in ERROR.

To use the app in debug mode on Mac:

1. Open a terminal window or a command prompt.

1. Launch the [!DNL Experience Manager] desktop app by running the following command:

    `AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app`.

To enable debug mode on Windows:

1. Open a command window.

1. Launch the [!DNL Experience Manager] desktop app by running the following command:

`AEM_DESKTOP_LOG_LEVEL=DEBUG&"C:\Program Files\Adobe\Adobe Experience Manager Desktop.exe`.

### Know the [!DNL Adobe Experience Manager] desktop app version {#know-app-version-v2}

To see the version number:

1. Start the application.

1. Click the ellipses in the upper right corner, hover over [!UICONTROL Help], then click [!UICONTROL About].

    The version number is listed on this screen.

### Clear cache {#clear-cache-v2}

Perform the following steps:

1. Start the application and connect to an instance of [!DNL Experience Manager].

1. Open the application's preferences by clicking the ellipses in the upper right corner and selecting [!UICONTROL Preferences].

1. Locate the entry displaying the [!UICONTROL Current Cache Size]. Click the trash icon next to this element.

To clear the cache manually, do the following: 

>[!CAUTION]
>
>These steps are a potentially destructive operation. If there are local file changes that are not uploaded to [!DNL Adobe Experience Manager], then those changes are lost.

The cache is cleared by deleting the application's cache directory, which is found in the application's preferences.

1. Start the application.

1. Open the application's preferences by selecting the ellipses in the upper right corner and selecting [!UICONTROL Preferences].

1. Note the [!UICONTROL Cache Directory] value.

    In this directory, there are subdirectories named after the Encoded [!DNL Adobe Experience Manager] Endpoints. The names are an encoded version of the targeted [!DNL Adobe Experience Manager] URL. For example, if the application is targeting `localhost:4502`, then the directory name is `localhost_4502`.

To clear the cache, delete the desired Encoded [!DNL Adobe Experience Manager] Endpoint directory. Alternatively, deleting the entire directory specified in the preferences clears the cache for all instances that have been used by the application.

Clearing [!DNL Adobe Experience Manager] desktop app's cache is a preliminary troubleshooting task that can resolve several issues. Clear the cache from the app preferences. See [set preferences](install-upgrade.md#set-preferences). The default location of the cache folder is:

## Cannot see placed assets {#placed-assets-missing}

If you cannot see the assets that you or other creative professionals placed in the support files (say, INDD files), check the following:

* Connection to the server. Flaky network connectivity can stall asset downloads.

* File size. Large assets take longer to download and display.

* Drive letter consistency. If you or another collaborator placed the assets while mapping the [!DNL Experience Manager] DAM to a different drive letter, the placed assets do not display.

* Permissions. To check if you have permissions to fetch the placed assets, contact your [!DNL Experience Manager] administrator.

### Edits to files on the desktop app's user interface do not reflect in [!DNL Adobe Experience Manager] immediately {#changes-on-da-not-visible-on-aem}

[!DNL Adobe Experience Manager] desktop app leaves it up to the user to decide when all edits to a file are complete. Depending on the size and complexity of a file, it takes a significant amount of time to transfer the new version of a file back to [!DNL Adobe Experience Manager]. The application is designed to minimize the number of file transfers, rather than automatically uploading files based on guessed completion of edits. It is advised that the user initiate the transfer of the file back to [!DNL Adobe Experience Manager] by choosing to upload a file's changes.

### Issues when upgrading on macOS {#issues-when-upgrading-on-macos}

Occasionally, issues may occur when upgrading the [!DNL Experience Manager] desktop app on macOS. Legacy system folders for the [!DNL Experience Manager] desktop app cause these issues. The folders prevent new versions of the [!DNL Experience Manager] desktop app to load correctly. To remedy this issue, the following folders and files can be manually removed.

Before running the following steps, drag the `Adobe Experience Manager Desktop` application from the macOS Applications folder to the Trash. Then open the terminal, run the following command, and provide your password when prompted.

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

## Cannot upload files {#upload-fails}

If you are using the desktop app with [!DNL Experience Manager] 6.5.1 or later, upgrade S3 or Azure connector to version 1.10.4 or later. It resolves the file upload failure issue related to [OAK-8599](https://issues.apache.org/jira/browse/OAK-8599). See [install instructions](install-upgrade.md#install-v2).

## [!DNL Experience Manager] desktop app connection issues {#connection-issues}

If you are experiencing general connectivity issues, here are some ways to get more information about what the [!DNL Experience Manager] desktop app is doing.

**Check the request log**

The [!DNL Experience Manager] desktop app logs all requests that it sends, along with each request's response code, in a dedicated log file.

1. Open `request.log` in the application's log directory to see these requests.

1. Each line in the log represents either a request or a response. Requests have a `>` character followed by the URL that was requested. Responses have a `<` character followed by the response code and the URL that was requested. Requests and Response can be matched using each line's GUID.

**Check requests loaded by the application's embedded browser**

A majority of the application's requests are found in the request log. However, if there is no helpful information there, then it can be useful to look into the requests sent by the application's embedded browser.
See the [SAML section](#da-connection-issue-with-saml-aem) for instructions on how to view those requests.

### SAML login authentication not working {#da-connection-issue-with-saml-aem}

[!DNL Experience Manager] desktop app may not connect to your SSO-enabled (SAML) [!DNL Adobe Experience Manager] deployment. The application's design attempts to accommodate the variations and complexities of SSO connections and processes. However, a setup may require additional troubleshooting.

Sometimes the SAML process does not redirect back to the originally requested path. Or, the final redirect is to a host that is different than what is configured in the [!DNL Adobe Experience Manager] desktop app. To verify that this issue is not the case, do the following:

1. Open a Web browser. Access `https://[aem_server]:[port]/content/dam.json` URL.

1. Log in to the [!DNL Adobe Experience Manager] deployment.

1. When the login is complete, look at the browser's current address in the address bar. It should exactly match the URL that was initially entered.

1. Also verify that everything before `/content/dam.json` matches the target [!DNL Adobe Experience Manager] value configured in [!DNL Adobe Experience Manager] desktop app's settings.

**Login SAML process works correctly according to the above steps, but users are still unable to log on**

The window within the [!DNL Adobe Experience Manager] desktop app that displays the login process is simply a web browser that is displaying the target [!DNL Adobe Experience Manager] instance's web user interface:

* The Mac version uses a [WebView](https://developer.apple.com/documentation/webkit/webview).

* The Windows version uses Chromium-based [CefSharp](https://cefsharp.github.io/).

Ensure that the SAML process supports those browsers.

To troubleshoot further, it is possible to view the exact URLs that the browser is attempting to load. To see this information:

1. Follow the directions for launching the application in [debug mode](#enable-debug-mode).

1. Reproduce the login attempt.

1. Navigate to the [log directory](#check-log-files-v2) of the application.

1. For Windows:

    1. Open "aemcompanionlog.txt."

    1. Search for messages that begin with "Login browser address changed to." These entries also contain the URL that the application loaded.

   For Mac:

    1. In `com.adobe.aem.desktop-nnnnnnnn-nnnnnn.log`, whichever numbers are in the newest file name replace **n**.

    1. Search for messages that begin with "loaded frame." These entries also contain the URL that the application loaded.

Looking at the URL sequence that is being loaded can help troubleshoot at the SAML's end to determine what is wrong.

### SSL configuration issue {#ssl-config-v2}

The libraries that the [!DNL Experience Manager] desktop app uses for HTTP communication uses strict SSL enforcement. At times, a connection may succeed using a browser but fails when using the [!DNL Experience Manager] desktop app. To configure SSL appropriately, install the missing intermediate certificate in Apache. See [How to install an Intermediate CA cert in Apache](https://access.redhat.com/solutions/43575).

The libraries that the [!DNL Experience Manager] desktop app uses for HTTP communication use strict SSL enforcement. So, there can be instances where SSL connections that succeed through a browser fail with the [!DNL Adobe Experience Manager] desktop app. This outcome is good because it encourages correct configuration of SSL and increases security, but can be frustrating when the application is unable to connect.

The recommended approach in this case is to use a tool to analyze a server's SSL certificate and identify issues so they can be corrected. There are Web sites that inspect a server's certificate by providing its URL.

As a temporary measure, it is possible to disable strict SSL enforcement in the [!DNL Adobe Experience Manager] desktop app. This approach is not a recommended long-term solution, as it reduces security by hiding the root cause of incorrectly configured SSL. To disable strict enforcement:

1. Use the editor of your choice to edit the application's JavaScript configuration file, which is found (by default) at the following locations (depending on the operating system):

    On Mac: `/Applications/Adobe Experience Manager Desktop.app/Contents/Resources/javascript/lib-smb/config.json`

    On Windows: `C:\Program Files (x86)\Adobe\Adobe Experience Manager Desktop\javascript\config.json`

1. Locate the following section in the file:

    ```shell
    ...
    "assetRepository": {
        "options": {
    ...
    ```

1. Modify the section by adding `"strictSSL": false` as follows:

    ```shell
    ...
    "assetRepository": {
        "options": {
            "strictSSL": false,
    ...
    ```

1. Save the file and restart the [!DNL Adobe Experience Manager] desktop app.

### Login issues when switching to a different server {#cannot-login-cookies-issue}

After using an [!DNL Experience Manager] server, when you attempt to change the connection to a different server, you may encounter login issues. It is due to old cookies interfering with new authentication. An option in the main menu to [!UICONTROL Clear Cookies] helps. Logout of the current session in the app and select [!UICONTROL Clear Cookies] before proceeding to connect.

![Clear cookies when switching server](assets/main_menu_logout_da2.png)

## App is unresponsive {#unresponsive}

Rarely the application may become unresponsive, display just a white screen, or display an error at the bottom of the interface without any options on the interface. Try the following in the order:

* Right click on the application interface and click **[!UICONTROL Refresh]**.
* Exit the application and open it again.

In both methods, the app starts at the root DAM folder.

## Hide expired assets {#hide-expired-assets}

When browsing assets from within the [!DNL Experience Manager] user interface, the expired assets are not displayed. Administrators can configure settings to prevent viewing, searching, and fetching of expired assets when browsing from the desktop app and Asset Link. Doing so ensures that expired assets are not accessible during these operations. The configuration works for all users, irrespective of administrator privilege.

* [Configuration in Experience Manager 6.5 to hide expired assets](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/managing/manage-assets#hide-expired-assets-via-acp-api).
* [Configuration in Experience Manager as a Cloud Service to hide expired assets](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/manage/manage-digital-assets#hide-expired-assets-via-acp-api).

<!--
### Need additional help with [!DNL Experience Manager] desktop app {#additional-help}

Create Jira ticket with the following information:

* Use `DAM - Companion App` as the [!UICONTROL Component].

* Detailed steps to reproduce the issue in [!UICONTROL Description].

* DEBUG level logs that were captured while reproducing the issue.

* Target Experience Manager version.

* Operating system version.

* [!DNL Adobe Experience Manager] desktop app version. To know your app version, see [finding the desktop app version](#know-app-version-v2).
-->

>[!MORELIKETHIS]
>
>* [Known issues](release-notes.md#known-issues-v2)
>* [Avoid editing conflicts](using.md#adv-workflow-collaborate-avoid-conflicts)
