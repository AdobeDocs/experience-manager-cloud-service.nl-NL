---
title: Manage Licensed Assets on Content Hub
description: Learn about various metadata management and editing methods
source-git-commit: 541d5819e19c67eb3f961e41000106178bff66de
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# Manage Licensed Assets on Content Hub {#manage-licensed-assets-on-content-hub}

As an administrator, edit the metadata form to include the asset license field so that it displays in Asset properties in AEM author environment. You can then approve the asset as well as its license to make the asset licensed and available on Content Hub.

Execute the following steps:

1. Edit the metadata form to include a new text field to include the license details. `dc:license` [](/help/assets/metadata-assets-view.md#metadata-forms)
   ![](/help/assets/assets/metadata-form-edit.png)
1. Apply the metadata form to the asset folder to apply the settings incorporated in step 1. [](/help/assets/metadata-assets-view.md#metadata-forms)
1. [Approve the licensed PDF](/help/assets/manage-organize-assets-view.md#set-asset-status)
1. **** In the license field added in Step 1, define the absolute path for the asset license that has been approved in step 3 or already approved earlier. `/content/dam/(The asset's folder hierarchy within the DAM repository)/(asset_name).(file_extension)` For example, /content/dam/teamA/projects/documents/file1.pdf
   ![](/help/assets/assets/absolute-path.png)


