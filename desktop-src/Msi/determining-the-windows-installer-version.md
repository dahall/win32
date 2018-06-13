---
Description: 'You can use the following methods to determine the Windows Installer version:'
ms.assetid: 6b39bb19-4360-4d0e-a797-980912a91275
title: Determining the Windows Installer Version
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# Determining the Windows Installer Version

You can use the following methods to determine the Windows Installer version:

-   Call the [**MsiGetFileVersion**](/windows/desktop/api/Msi/nf-msi-msigetfileversiona) function with the *szFilePath* parameter set to the path to the file Msi.dll.

    You can call the [**SHGetKnownFolderPath**](https://msdn.microsoft.com/windows/desktop/5434c744-484b-4c34-9a76-dddbcb81eb29) function with the **CSIDL\_SYSTEM** constant to get the path to Msi.dll. Beginning with Windows Vista, applications should use the [**SHGetFolderPath**](https://www.bing.com/search?q=**SHGetFolderPath**) function and the **REFKNOWNFOLDERID** "System." Existing applications that use the **SHGetFolderPath** function and the **CSIDL** type will continue to work.

-   The value of the [**Installer.Version**](installer-version.md) property of the [**Installer Object**](installer-object.md) is equivalent to the four-field strings listed in the [Released Versions of Windows Installer](released-versions-of-windows-installer.md) topic.
-   Applications can get the Windows Installer version by using [**DllGetVersion**](https://www.bing.com/search?q=**DllGetVersion**).
-   The installer sets the [**VersionMsi**](versionmsi.md) property to the version of Windows Installer that is run during the installation.

For more information, see [Released Versions of Windows Installer](released-versions-of-windows-installer.md).

 

 


