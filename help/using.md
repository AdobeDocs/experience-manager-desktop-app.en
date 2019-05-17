---
title: Use AEM desktop app
seo-title: Use Adobe Experience Manager desktop app
description: Learn how to install and use Adobe Experience Manager desktop app, to work on AEM assets right from your Win or Mac desktop. Know best practices and troubleshooting information.
seo-description: Learn how to install and use Adobe Experience Manager desktop app, to work on AEM assets right from your Win or Mac desktop. Know best practices and troubleshooting information.
uuid: 55057617-89de-43cd-8419-1252a42ab2fb
contentOwner: asgupta
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
products: SG_EXPERIENCEMANAGER/6.3
products: SG_EXPERIENCEMANAGER/6.2
products: SG_EXPERIENCEMANAGER/6.0
topic-tags: aem-desktop-app
discoiquuid: 39d7bcad-d7b0-4978-a790-4cb68b8a7d6a
index: y
internal: n
snippet: y
---

# Use AEM desktop app {#use-aem-desktop-app-v2}

Use the Adobe Experience Manager (AEM) desktop app, to easily access the AEM assets on your local desktop and use these assets in any desktop applications. You can open the assets in desktop applications and edit the assets locally – upload the changes back to AEM with version control, to share the updates with other users. You can also upload new files and folder hierarchies to AEM, create folders, and delete assets or folders from AEM.

The integration allows various roles in the organization to manage the assets centrally in AEM Assets and to access the assets on local desktop in the native applications on Windows or Mac OS.

When you open the application after logging out or for the first time, provide the URL of your AEM server. Click Connect. Provide your credentials to connect the app with the server.

The key tasks you do using the AEM desktop app are:

![Workflows and tasks you can accomplish using AEM desktop app](assets/whats-new-desktop-app-v2.png "Workflows and tasks you can accomplish using AEM desktop app")

## How desktop app works {#how-app-works2}

Before you start using the application, understand [How the app works](release-notes.md#how-app-works).

## Enable desktop actions in AEM web interface {#desktopactions-v2}

From within the Assets UI in a browser, you can explore the asset locations or check-out and open the asset for editing in your desktop application. These options are called Desktop Actions and are not enabled by default. Follow these steps to enable it.

1. In the Assets console, click/tap the **User** icon from the toolbar.
1. Click/tap the **[!UICONTROL My Preferences]** to display the **[!UICONTROL Preferences]** dialog.
1. In the User Preferences dialog, select **[!UICONTROL Show Desktop Actions For Assets]**. Click/tap **[!UICONTROL Accept]**.

   ![Check Show Desktop Actions For Assets to enable desktop actions](assets/chlimage_1-3.png)

   Check Show Desktop Actions For Assets to enable desktop actions

## Browse, search, and preview assets {#browse-search-preview-assets}

You can browse to, search for, and preview the assets available in the AEM repository, all from within the desktop application. Try the following in the app:

1. Browse to a folder and see some basic info of the assets available in the folder, along with small thumbnails of all assets.

   ![Browse the DAM files and folders](assets/browse_folder_da2.png "Browse the DAM files and folders")

1. To view more information and a larger thumbnail of an individual asset, click the file name.

   ![See a larger preview of an asset and actions](assets/large_preview_actions_da2.png "See a larger preview of an asset and actions")

1. Click Open or Edit to download the file locally and just view it or edit it in the native application, respectively.
1. Search using keywords to find a related asset in the AEM repository. Use ‘?’ and ‘*’ with keyword as wildcards to substitute for a single character or for multiple characters. Filter and sort the results as required.

   ![Sample search using asterisk wildcard](assets/search_wildcard_da2.png "Sample search using asterisk wildcard")

   ![Another sample search using asterisk wildcard](assets/search_wildcard2_da2.png "Another search - be cautious of creating queries using wildcard")

>[!NOTE]
>
>The app displays the assets by matching the search criteria across multiple metadata fields and not just the asset’s title or the file name.

## Download assets {#download-assets}

You can download the assets on your local filesystem. The app fetches the assets from AEM server and saves the same copy on your local filesystem.

Click ![More options icon](assets/do-not-localize/more2_da2.png) for options and click ![Download icon](assets/do-not-localize/download_cloud_da2.png) to download.

![Download option for an asset](assets/download_option_da2.png "Download option for an asset")

>[!NOTE]
>
>When downloading or uploading a larger number of files, the application might turn off the actions on assets and folders. The actions are available when the download operation completes.

Downloading multiple assets may lead to poor performance if queue size is large or if you face some network issue. Also, you may unknowingly queue many assets for download when you download a folder. To avoid long wait times, the app restricts the number of assets downloaded in one go. To know how to configure it, see [Set preferences](install-upgrade.md#set-preferences). Even below this limit, the app may at times seek a confirmation before downloading an apparently large folder.

![App confirms download of relatively large number of assets to avoid long wait times](assets/download_confirmation_da2.png "App confirms download of relatively large number of assets to avoid long wait times")

## Open assets on your desktop {#openondesktop-v2}

You can open the remote assets for viewing in the native application. The assets are downloaded to a local folder and launched in the native application associated with the file format.

Access the Open option in the more menu by clicking  . The asset is downloaded locally and opened in the native application. Check the download progress and transfer speed of large assets in the status bar.
![Download progress bar for large-sized assets](assets/download_status_bar_da2.png "Download progress bar for large-sized assets")

>[!NOTE]
>
>Clicking ![Close icon](assets/do-not-localize/close_da2.png) in the status bar does not stop or cancel the download. If the expected changes are not reflected in the app, click refresh icon ![Refresh icon](assets/do-not-localize/refresh.png) . Also note that the actions are not available while larger downloads or uploads are in progress.

To open the local download folder of an asset, click ![More actions icon](assets/do-not-localize/more2_da2.png) and click ![Reveal icon](assets/do-not-localize/reveal_action2_da2.png) Reveal action.

## Use or place assets into native documents {#place-assets-in-native-documents}

To directly see the filesystem location of the locally downloaded files, use the ![Reveal icon](assets/do-not-localize/reveal_action2_da2.png) Reveal File option.

![Reveal File action for an asset](assets/revealfile_action_da2.png "Reveal File action for an asset")

Click Reveal File, or Reveal on a folder, to open Windows Explorer or Mac Finder with the file or folder preselected on your local machine. The option is useful to, say place the AEM files in the native applications that support placing or linking local files. To see how to place files in Adobe InDesign, see [Placing graphics](https://helpx.adobe.com/indesign/using/placing-graphics.html).

The “Reveal” location shows a local network share, showing only the files that are available locally – that is, it will only show files that were revealed, downloaded, or opened/edited using the AEM desktop app actions. The network share will also not automatically upload any changes – you need to use “Upload Changes” or “Upload” actions in the AEM desktop app to do that.

>[!NOTE]
>
>For backwards compatibility with AEM desktop app v1.x, the files revealed are served from a local network share, exposing locally available files only. The desktop paths of the revealed files are the same as the paths created by app v1.x. If required, customize the drive letter, from the [app Preferences](install-upgrade.md#set-preferences).

>[!CAUTION]
>
>Do not use Reveal File option to edit assets in native applications. Instead, use the Edit actions. To know more, see Advanced workflow: collaborate on same files and avoid editing conflicts.

## Edit assets and upload updated assets to AEM {#edit-assets-upload-updated-assets}

Open assets for editing when you want to make changes and upload the updated assets to AEM server. To avoid conflicts with edits of other users, use the app to initiate an editing session. Click the Edit option that will open the asset in the native application associated with the asset. Ensure that the asset you start editing does not have a lock icon on it, that is, the asset is not being edited by another user.

To edit an asset, search for the asset or browse to the asset’s location. Click ![More icon](assets/do-not-localize/more2_da2.png) and click Edit.

<!-- ![](assets/.png "Edit action in preview")
!-->

If you start editing an asset without checking it out (say by just opening it), use Toggle check-out option to lock the asset to prevent conflicts with edits of other users. You can use Toggle check-out option on an asset that you intend to start editing soon and do not want others to edit.

Once you’re done making the edits, the app displays the Edited Locally status for the changed assets. All the changes saved to the assets are local-only until you upload the changes to AEM. To upload an individual or a few assets one-by-one, click Upload Changes from the options for an asset. It creates a version of the asset in AEM. Using the web interface of AEM Assets, you can see asset history in the [Timeline view](https://helpx.adobe.com/experience-manager/6-4/assets/using/activity-stream.html).

![Upload changes option in the app](assets/upload_changes_single1_da2.png "Upload changes option in the app")

![Upload changes option when viewing a large preview of an asset](assets/upload_changes_single2_da2.png "Upload changes option when viewing a large preview of an asset")

For best practices around collaborative editing, see [Advanced workflow: collaborate on same files and avoid editing conflicts](#adv-workflow-collaborate-avoid-conflicts).

## Upload and add new assets to AEM {#upload-and-add-new-assets-to-aem}

You may be required to add new assets to the repository. For example, you may be an agency photographer or contractor who must add a large number of photos from a photoshoot to the AEM repository. To upload assets in bulk to add fresh content to AEM, click ![Upload to cloud icon](assets/do-not-localize/upload_to_cloud_da2.png) in the top-bar of the app. Browse to the asset files in the local filesystem and click Select. The app starts uploading the asset and displays a progress bar at the bottom if the asset takes longer to upload.

![Download progress bar for large-sized assets](assets/upload_status_da2.png "Download progress bar for large-sized assets")

You can upload folders or individual files from your local filesystem. A folder’s hierarchy is preserved when it is uploaded.

To view the list of assets transferred in a given session, click View > Assets transfer. The list allows you to quickly verify the file transfers of the current session.

![List of transferred assets in a particular session](assets/assets_transfered_da2.png "List of transferred assets in a particular session")

>[!NOTE]
>
>The transfer list is not persistent and is not available if you exit the app and re-open it.

## Work with multiple assets {#work-with-multiple-assets}

Users can easily work with and manage multiple assets using actions like uploading all edits in one go or uploading nested folders in a few clicks.

### Browse large folders {#browse-large-folders}

When working with folders containing many assets, scroll to view more assets. To scroll using the keyboard, press tab a few times to select the asset at the top. Notice the highlighted asset to know when it is selected. Now use the Down arrow key to move through the list of assets.

### Quick actions for selected assets {#quick-actions-for-selected-assets}

Click on the thumbnail of a few assets to select. To select all assets, click the checkbox in the top-bar of the app. The set of actions that are applicable to all the selected assets collectively are displayed in a toolbar at the bottom of the app.

![Toolbar at the bottom shows actions relevant to the selected assets](assets/actions_bottom_toolbar1_da2.png "Toolbar at the bottom shows common actions for the selected assets")

![No actions in toolbar when no common actions for the selection](assets/actions_bottom_toolbar2_da2.png "No actions in toolbar when no common actions for the selection")

Actions available in the toolbar at the bottom depend on the status of selected files. For example, if you only select **Edited Locally** files, you see **Upload Changes** icon. If you select a mix of **Edited locally** and **Cloud only**, the **Upload Changes** action is not available.

### Find all edited images {#find-all-edited-images}

The application provides a view, called ‘Edited locally’, to give you quick access to all the files that you downloaded locally (via Open or Edit action) and then modified as files on your local system. The app allows to select all locally edited assets and upload the changes in a few clicks. This view also includes the locally edited images that have an editing conflict.

![Filter to see all the locally edited assets](assets/edited_locally_filter_da2.png "Filter to see all the locally edited assets, say for bulk upload of edits")

### Bulk upload assets {#bulk-upload-assets}

Users or organization, such as photographers or creative agencies, who create a lot of local assets can now upload large local folders to AEM Assets directly from the desktop app. The folder hierarchies are preserved and all the nested sub-folders and included assets are uploaded. The uploaded assets are immediately available to other users of the same server for consumption as well.

![Bulk upload multiple local folders from your desktop into AEM](assets/upload_local_folders_da2.png "Bulk upload multiple local folders from your desktop into AEM")

After uploading, if the expected changes are not reflected in the app, click the refresh icon ![Refresh icon](assets/do-not-localize/refresh.png).

### List of transferred assets {#list-of-transferred-assets}

To view the list of assets transferred in a given session, see [Upload assets to AEM](#upload-and-add-new-assets-to-aem).

## Advanced workflow: start from the AEM Assets web interface {#adv-workflow-start-from-aem-ui}

You can initiate your workflow from the AEM Assets web interface. The desktop app not only supports all workflows but also integrates with the Assets UI to simplify your workflows.

A special case of starting workflow from the web interface is asset discovery. The Omnisearch bar in Assets UI offers a rich and advanced search experience. You may want to first locate a desired asset on the web and then initiate the workflow in the app, using Desktop Actions. Some sample cases include filtering search results using facets, locating a specific asset licensed from Adobe Stock, or a customization implemented by your organization that allows you better discovery from the web interface.

One or more desktop app functionalities are invoked when you attempt these actions on the web:

* The Desktop Actions Open, Edit, and Reveal 
* Upload folder
* Check-out or check-in

For example, the actions on the web interface that are available for an asset that is checked out in the app are Open, Reveal, and Check-in.

![Desktop Actions in the AEM web interface](assets/assets_web_actions_da2.png "Desktop Actions in the AEM web interface")

>[!NOTE]
>
>The browser may prompt you to permit the launch of Adobe Experience Manager Desktop. To enjoy uninterrupted transfer from the browser to the app, select the appropriate checkbox to always allow the app to take over.

You cannot find the following information or workflow using the web interface. Use the desktop app as the web interface is not completely aware of the local changes and hence of the following:

* Files edited locally.
* Files that have an editing conflict and way to resolve it.
* Upload local changes to AEM.
* Various statuses of the locally available files.

## Advanced workflow: collaborate on same files and avoid editing conflicts {#adv-workflow-collaborate-avoid-conflicts}

In collaborative environments, multiple users may work on same set of assets that can lead to versioning conflicts. To prevent conflicts, follow these best practices:

* Do not edit any assets by clicking Open. Do not edit the locally downloaded assets by opening from your filesystem folder. Other users do not know that the asset is being edited.
* To edit an asset, always click Edit. It opens the asset in the native application and adds a lock icon on the asset, so the other users know that the asset is being edited.
* Click Toggle check-in if you accidentally start editing without click Edit. It will add a lock icon to the asset. Even if you plan to edit an asset later but want to avoid others editing it, click Toggle check-in to lock the asset.
* Before editing an asset, ensure that other users are not editing it. Look for the lock icon on the asset.
* After completing the edits, upload all the changes, and then check-in the asset

![Statuses of editing conflicts](assets/edits_conflicts_status_da2.png "Statuses of editing conflicts")

If a locally downloaded asset is updated on the AEM server, the app displays a **Modified remotely** status. You can either remove your local copy or refresh your local copy, by clicking Remove or Update respectively. Links on the dialog allow you to view both versions of the asset.

![Options to resolve the conflict when the asset is remotely modified](assets/modified_remotely_dialog_da2.png "Options to resolve the conflict when the asset is remotely modified")

If an asset you are editing locally is also updated on the server without your knowledge, the app displays an ‘Editing Conflict’ status. You can retain one set of the changes – either retain your updates (click **Keep Mine**) and delete the other user’s edit or respect the other user’s updates and delete yours (**Overwrite Mine**).

![Options to resolve an editing conflict](assets/editing_conflict_dialog_da2.png "Options to resolve an editing conflict")

## Advanced workflow: place and link assets in InDesign file {#adv-workflow-place-assets-indesign}

When you use AEM desktop app to open files with linked assets, the assets are pre-downloaded and appear placed in the native applications. For this workflow to work, your native application must support placing links to local assets and AEM must support resolving these links in the binary files to server-side references.

AEM desktop app supports this workflow with a few select Adobe Creative Cloud desktop applications and file formats – InDesign, Illustrator, and Photoshop. The workflow allows you to work efficiently with the supported Creative Cloud files. So if user A places a few assets in an InDesign file and checks it into AEM, user B sees the assets in the InDesign file even though the assets are not part of the file. The assets are locally downloaded on the machine of user B.

>[!NOTE]
>
>The desktop app can map to any drive. However, for smooth operations, do not change the default drive mapping. You may not be able to see the placed assets if you change the drive letter. However, the assets are not removed and continue to be placed in the file.

To know the limitations of this workflow, see the [System requirements and supported versions](release-notes.md#system-requirements-and-prerequisites-v2).

To try this workflow with an image asset and InDesign, follow these steps:

1. Keep handy an INDD file with placed assets in AEM. To know how to create such an INDD file, see [Placing Graphics](https://helpx.adobe.com/indesign/using/placing-graphics.html).
1. From within desktop app, Edit the INDD file with placed assets in AEM.
1. Note that the desktop app downloads both, the InDesign file and the linked assets. When InDesign opens the document, the links are resolved, assets are downloaded, and the assets are displayed in the InDesign document.
1. To place a new graphic in the InDesign file, use Reveal File action on the asset. The action downloads the asset locally and opens the local network share location in Windows Explorer or Mac Finder.
1. Place the revealed asset in the InDesign document. This creates a new link in the document.
1. Once you complete your edits in the InDesign document, save it and upload it to AEM using the desktop app.

## Advanced workflow: download the assets locally {#adv-workflow-download-assets-locally}

The app downloads the assets from AEM server locally on your filesystem in many scenarios that you should be aware of. The downloads consume bandwidth and disk space. Knowing the scenarios will help you optimize your wait time for the downloads to complete.

You download the assets from within the app on-demand. See [Download assets](#download-assets).

When you use the Open action to open an asset in a native desktop application, the asset is downloaded locally if not already available locally. See [Open assets](#openondesktop-v2).

When you reveal the location of an asset or a folder from within the app, the asset or the folder is first downloaded locally and then opened on your machine in the local network share. See [Open assets](#openondesktop-v2).

When you use the edit action to edit an asset in a native desktop application, the asset is downloaded locally if not already available locally. See [Edit assets and upload updated assets to AEM](#edit-assets-upload-updated-assets).

When you use Desktop Actions from AEM web interface, the actions are completed by the app if the app is installed and is permitted to complete the actions. The asset is first downloaded by the app and then the action is completed.