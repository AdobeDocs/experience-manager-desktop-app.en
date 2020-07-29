---
title: Use AEM desktop app version 1.x.
description: Learn how to use Adobe Experience Manager desktop app version 1.x and optimize your work with assets on desktop.
contentOwner: AG
---

# Use AEM desktop app v1.x {#use-aem-desktop-app-v1x}

Using the App, the assets within AEM are easily accessible on your local desktop and can be used in any desktop applications. Assets can be easily revealed in Mac Finder or Windows Explorer, opened in desktop applications, and changed locally - the changes are saved back to AEM with a new version created in the repository.

Such an integration allows various roles in the organization to manage the assets centrally in AEM Assets and to access them in the Creative Cloud and other applications, while making it easy to adhere to the various standards including branding.

The key tasks you do using the AEM desktop app v1 include:

1. [Connect with an AEM server](#installandconnect)
1. [Open assets directly on desktop](#openondesktop)
1. [Edit and check out assets from desktop](#workonassets)
1. [Upload assets and folders in bulk](#bulkupload)

For the various recommended dos and don'ts, see the [best practices for using app](best-practices-for-v1.md). If you face issues using the App, see how to [troubleshoot AEM desktop](troubleshoot-app-v1.md).

>[!NOTE]
>
>AEM desktop app was introduced in AEM 6.1 release and was called AEM Assets Companion App.

## AEM desktop app touch-points in the creative workflow {#aem-desktop-app-touch-points-in-the-creative-workflow}

AEM Desktop app, along with AEM Assets, integrates in your creative workflow and offers the following touch-points.

![AEM Desktop app touch-points the creative workflow](assets/aem_desktopapp_workflow.png)

AEM Desktop app touch-points the creative workflow

## Install and connect AEM desktop app to AEM server {#installandconnect}

Before you can begin creating or editing the creative assets, connect the desktop application with the AEM Assets server to download and upload assets in the repository. Perform the following tasks:

1. [Install the app](#installapp).
1. [Set your preferences](#inapppref) and connection details.
1. [Connect to an AEM server](#connect) and mount assets repository as local drive.
1. [Enable desktop actions](#desktopactions) on AEM server.

AEM desktop app uses an HTTPS connection to connect to AEM server to robustly and securely transfer your assets.

>[!NOTE]
>
>For part of or all of the installation and configuration steps, you may need help from your AEM administrator or system administrator.

### Install the application {#installapp}

To use AEM desktop app, ensure that your AEM server version is supported by AEM Desktop app. Download the appropriate installation file (binary) for your operating system (Mac or Windows) and install the app.

Detailed configuration can be necessary depending on your network and system preferences. See [Install and configure AEM Desktop app](install-configure-app-v1.md) for more details.

1. Go to the [AEM Desktop app download page](https://helpx.adobe.com/experience-manager/kb/download-companion-app.html) and download the appropriate binary for your operating system.
1. Launch the downloaded installation file and follow the on-screen instructions to install the app.

   >[!NOTE]
   >
   >Only one instance of the AEM desktop app can be installed and be active at a time.

### Understand the in-app options and preferences {#inapppref}

The application allows for settings to connect and disconnect from AEM servers, view status of uploads, manage local cache, and so on. The default settings work for a typical user of the application. You can tweak the settings to get more out of the application and out of the integration with AEM server. The various settings are described below in details.

**Explore Assets** Open the local drive in which the AEM Assets repository is mounted. In other words, explore the assets that are now made available on your local machine.

**View asset status** When changed assets are uploaded or new assets are added to the AEM Assets repository, the application uploads the assets in the background. The background upload allows for smooth operations, without you having to wait for the upload to finish, especially for large-sized assets. You can save your changes locally and forget it. The application takes some time to send these assets to the server, depending on the available bandwidth. You can check the status of the upload, along with some more basic information.

**Options** Click/tap Options from the AEM Desktop app tray to access settings to launch the application when your system starts; to connect to the AEM server when the app is launched; and to change the local drive letter where AEM Assets is available after mounting.

**Advanced > Manage cache** You can control the amount of disk space made available for local caching purposes. The artifacts from the AEM Assets server are cached locally for a smoother experience. You can change the defaults to suit your requirements. Also, you can clear the cache to fetch all assets afresh. When you clear the cache, it preserves your unsaved changes. Any assets not checked into AEM server are retained and not deleted.

### Connect to an AEM server {#connect}

The app supports proxy configuration on Mac and Windows. The configuration is read when the app starts. If you modify proxy settings, restart the app for the changes to take effect.

>[!NOTE]
>
>If you modify the proxy settings, restart the app for the changes to take effect. Otherwise, the app continues to use the previously configured proxy server.

1. Launch AEM Desktop app. To map your AEM instance with the app, specify your AEM server in the format `https://[aem-server-url]:[port]`.

   ![Authenticate on Mac and provide AEM server URL](assets/aem_desktop_app_server_url.png)

1. In the login screen, specify the user name and password for your instance. To specify an alternate AEM instance, select the **[!UICONTROL Alternate Login URL]** option.

   ![Provide AEM server credentials on the login screen on AEM Desktop](assets/chlimage_1-2.png)

### Enable desktop actions in AEM web interface {#desktopactions}

From within the Assets user interface, you can explore the asset locations or check-out and open the asset for editing in your desktop application. These options are called desktop actions and are not enabled by default. Follow these steps to enable it.

1. In the Assets interface, click/tap the User icon in the upper right corner of the toolbar.
1. Click **[!UICONTROL My Preferences]** to display the **[!UICONTROL Preferences]** dialog.

   ![AEM interface with user preferences](assets/aem_ui_user_preferences.png)

1. In the User Preferences dialog, select **[!UICONTROL Show Desktop Actions For Assets]**. Click **[!UICONTROL Accept]**.

   ![Check Show Desktop Actions For Assets to enable desktop actions](assets/chlimage_1-3.png)

   *Figure: Check Show Desktop Actions For Assets to enable the desktop actions.*

## Access and open assets on your desktop {#openondesktop}

When you click **Open** to open an asset on local machine, the app downloads the asset to its internal cache. The app launches the native desktop application that is associated with the file type of the downloaded asset.

On Mac, select **Open** from the context menu to open an asset through AEM desktop app. On Windows, select Open on Web from the context menu to open the asset. From the Asset Status window, click/tap ![Open on Desktop icon](assets/aemassets_icon_openondesktop.png) to open the asset.

For Adobe InDesign (INDD) files, select **[!UICONTROL Open]** from the context menu. When you click this option, the App downloads the linked assets to your local file system and then opens the INDD file in Adobe InDesign. This method ensures that the necessary assets are locally available when editing the INDD file.

![Context menu options to access and open assets using AEM Desktop app](assets/aem_desktopapp_mac_context_menu.png)

*Figure: Context menu options to access and open assets using AEM desktop app.*

>[!NOTE]
>
>On Windows, the [default Windows 7 setting](https://support.microsoft.com/en-us/kb/2668751) prevents AEM desktop app from handling assets that are larger than 50 MB.

>[!NOTE]
>
>Adobe recommends that you go to Finder View Options on Mac and deactivate the options **Show item info**, **Show item preview**, and **Show preview column** for the mounted AEM Assets folder. It improves the performance.

### Additional options in AEM interface {#additional-options-in-aem-assets}

After you map the AEM Assets repository to your local drive, you can enable additional icons and the Folder Upload feature to appear for the mapped assets and folders.

1. Open the AEM Assets interface and hover the pointer over a folder or an asset, to display the desktop actions as quick actions in the Card view.

   ![In Assets UI, open quick actions menu to see desktop actions](assets/chlimage_1-4.png)

   *Figure: In Assets UI, open quick actions menu to see desktop actions.*

   These desktop actions are also available when you click the **Desktop Actions** icon in the toolbar after selecting the asset or from the toolbar in the asset page.

1. To open the asset in the desktop application that is associated with the specific file extension, click/tap the **Open on desktop** quick action ![Open on Desktop icon](assets/aemassets_icon_openondesktop.png).

   Alternatively, choose **Open** from the **Desktop Actions** menu in the toolbar.

To locate the particular asset on your local file system, click **Reveal** quick action ![Reveal icon](assets/aemassets_reveal_icon.png). Alternatively, choose **Reveal** from the **Desktop Actions** menu in the toolbar.

## Understand the asset statuses {#understand-the-asset-statuses}

| ![Windows default app icon](assets/win_default.png) | App is connected to the server and all assets are synchronized.                                                                                           |
|------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| ![Windows disabled icon](assets/win_disabled.png) | App is launched but is not connected with the server. Some assets may be pending synchronization.                                                         |
| ![Windows file sync icon](assets/win_sync.png) | Assets are synchronizing. Files are either being uploaded or downloaded. You can see exact statuses and pause the transfers from the Asset Status window. |
| ![Windows reconnect icon](assets/win_refresh.png) | App is trying to reconnect. Potentially the network issues are causing it to disconnect.                                                                  |

## Work on your assets {#workonassets}

### Check out assets from the AEM web interface {#check-out-assets-from-the-aem-web-interface}

AEM Assets lets you check out assets for editing and check them back in after you complete making the changes. After you check out an asset, only you can edit, annotate, publish, move, or delete the asset. Checking out an asset locks the asset and prevents other users from performing any of these operations. To be able to check out/in assets, you require Write access on them.

There are two ways of checking out assets from the AEM web interface. For detailed information on the first method, see [check in and checkout files from Assets UI](https://docs.adobe.com/content/help/en/experience-manager-65/assets/managing/check-out-and-submit-assets.html). Follow these steps, for the second methods to check out and open the asset when AEM Desktop app is installed.

1. Open the AEM Assets interface and hover the pointer over a folder or an asset, to display the desktop actions as quick actions in the Card view.

   ![Properties option in Card View](assets/chlimage_1-4.png)

   These desktop actions are also available when you click/tap the Desktop Actions icon in the toolbar after selecting the asset or from the toolbar in the asset page.

1. To open the asset, click/tap the Open on desktop quick action ![Open on Desktop icon](assets/aemassets_icon_openondesktop.png).

   Alternatively, choose Open from the Desktop Actions menu in the toolbar.

   >[!NOTE]
   >
   >When you edit a file that is just opened and not checked-out, other users do not get to know that an asset is being updated by you.

1. To open an asset for editing in an Adobe Creative Cloud application, click/tap the Edit desktop quick action ![Edit Desktop icon](assets/aemassets_icon_editdesktop.png). This also checks out the asset for editing. After you finish editing, check in the asset, to update the changes in AEM Assets.

   Alternatively, choose Edit from the Desktop Actions menu in the toolbar.

1. Select the Open menu option. The selected assets are opened in preview mode.
1. To edit the assets, select the Edit option. The assets are opened in edit mode.

### Check out assets from Finder on Mac OS {#check-out-assets-on-mac}

The app lets you check out asset files to prevent other users from modifying the files that you’re working on.

1. From the Mac context menu, select the Open AEM Assets Folder to open Finder.

   ![Context menu options to access and open assets using AEM Desktop app](assets/aem_desktopapp_mac_context_menu.png)

   Context menu options to access and open assets using AEM Desktop app

1. Navigate to the asset you want to check out.

   ![Open in AEM Assets context menu on Mac](assets/chlimage_1-5.png)

1. Right-click the asset, and select More Assets Info from the context menu.
1. In the Asset Info dialog, click/tap the Checkout icon to check out the asset. The Checkout icon toggles to the check-in icon after you click/tap it.

   ![Browse to asset to checkout](assets/chlimage_1-6.png)

1. To check in the asset so it is available to other users, click/tap the check-in icon in the Asset Info dialog.

### Check out assets on Windows {#check-out-assets-on-windows}

The app lets you check out asset files to prevent other users from modifying the files that you’re working on.

1. From the Context menu, select the Explore Assets to open Explorer.
1. In Explorer, navigate to the location of the asset you want to check out.

   ![Checkout icon toggles](assets/chlimage_1-7.png)

1. Right-click the asset and select Open on Web from the context menu.
1. In the Asset Info dialog, click/tap the Checkout icon. The Checkout icon toggles to check-in icon.

   ![Checkout icon toggles](assets/chlimage_1-8.png)

1. Review the asset in Explorer. The lock icon on the asset ![Asset lock icon](assets/aemassets_icon_lockcheckout.png) indicates that you have checked out the asset.

   >[!NOTE]
   >
   >The lock icon may appear after some delay. AEM desktop app caches the assets for quick access so it may take a few moments to update the locked status.

1. To check in the asset so it is available to other users, click/tap the check-in icon in the **Asset Info** dialog.

### Check in an asset using Finder or Explorer and using web interface {#check-in-an-asset-using-finder-or-explorer-and-using-web-interface}

When you've finished editing the assets, save the assets in your desktop application. From the context menu, select **More Assets Info** and click check-in.

The assets are uploaded to AEM server. Optionally, you can check the status of the upload by selecting **View Asset Status** from the system tray icon. Alternatively, you can check in an asset from the AEM web interface. Click the checked out assets or select it. From the toolbar, click the check in icon ![check-in icon](assets/aemassets_icon_checkin.png).

An asset is uploaded to AEM automatically after any changes are saved locally. The check-in makes the asset available to other AEM users for editing.

### Bulk upload assets and folders to AEM server {#bulkupload}

Using AEM Desktop, you can upload an entire folder containing assets from your local file directory to AEM Assets. This way, all assets within the folder are uploaded in bulk instead of having to upload them one at a time.

1. From the Assets UI, click/tap **Create** from the toolbar, and the choose **Upload Folder** from the menu.
1. Browse to the folder you want to upload and select it.
1. Click/tap OK. The Assets Status dialog displays the status of the upload.

   ![See status of the upload in the Asset Status window](assets/aem_desktopapp_bulkupload_status.png)

   See status of the upload in the Asset Status window

   >[!NOTE]
   >
   >You can manually pause or cancel the upload by clicking/tapping the appropriate icon.

1. After the folder uploads, close the dialog and navigate to the Assets UI. The uploaded folder is displayed in the web interface.

Adobe does not recommend to copy-paste or drag larger number of files or nested folders, from the local file system, into the network share area. The app cannot control the upload process due to technical limitations and the performance is poor.

Alternatively, select files/folders you want to upload to AEM in Finder or Explorer, copy them to system clipboard, navigate to the target folder in the network share area, and from the AEM desktop app context menu select **Paste Assets**. This way, AEM desktop app starts uploading the pasted assets similar to the **Upload Folder** option available in the AEM web interface.

>[!MORELIKETHIS]
>
>* [Introduction to AEM desktop app](https://helpx.adobe.com/customer-care-office-hours/aem/desktop-app.html)
>* [Understand Check-in/check-out with AEM desktop app](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/collaboration/checkin-checkout-technical-video-understand.html)
>* [Troubleshoot AEM desktop app application](troubleshoot-app-v1.md)
