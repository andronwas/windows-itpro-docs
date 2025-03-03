---
title: About Client Configuration Settings (Windows 10)
description: About Client Configuration Settings
author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 04/18/2018
ms.reviewer: 
manager: dansimp
ms.author: dansimp
ms.topic: article
---
# About Client Configuration Settings

>Applies to: Windows 10, version 1607

The Microsoft Application Virtualization (App-V) client stores its configuration in the registry. Understanding how the register's format for data works can help you better understand the client, as you can configure many client actions by changing registry entries. This topic lists the App-V client configuration settings and explains their uses. You can use Windows PowerShell to modify the client configuration settings. For more information about using Windows PowerShell and App-V see [Administering App-V by using Windows PowerShell](appv-administering-appv-with-powershell.md).

You can use Group Policy to configure App-V client settings by navigating to the **Group Policy management console** at **Computer Configuration** > **Administrative Templates** > **System** > **App-V**.

## App-V Client Configuration Settings: Windows PowerShell

The following table provides information about App-V client configuration settings that can be configured through Windows PowerShell cmdlets:

| Windows PowerShell cmdlet or cmdlets,<br>**Option**<br>Type  | Description  | Disabled policy state keys and values |
|------------|------------|------------|------------|
| Set-AppvClientConfiguration,<br>Set-AppvPublishingServer<br><br>**-PackageInstallationRoot**<br>String  | Specifies directory where all new applications and updates will be installed.  | Policy value not written (same as Not Configured) |
| Set-AppvClientConfiguration,<br>Set-AppvPublishingServer<br><br>**-PackageSourceRoot**<br>String  | Overrides source location for downloading package content.  | Policy value not written (same as Not Configured) |
| Set-AppvClientConfiguration,<br>Set-AppvPublishingServer<br><br>**-AllowHighCostLaunch**<br>True (enabled); False (Disabled state)  | This setting controls whether virtualized applications are launched on Windows 10 machines connected by a metered network connection (for example, 4G).  | 0 |
| Set-AppvClientConfiguration,<br>Set-AppvPublishingServer<br><br>**-ReestablishmentRetries**<br>Integer (0–99)  | Specifies the number of times to retry a dropped session.  | Policy value not written (same as Not Configured) |
| Set-AppvClientConfiguration,<br>Set-AppvPublishingServer<br><br>**-ReestablishmentInterval**<br>Integer (0–3600)  | Specifies the number of seconds between attempts to reestablish a dropped session.  | Policy value not written (same as Not Configured) |
| Set-AppvClientConfiguration,<br>Set-AppvPublishingServer<br><br>**-LocationProvider**<br>String  | Specifies the CLSID for a compatible implementation of the IAppvPackageLocationProvider interface.  | Policy value not written (same as Not Configured) |
| Set-AppvClientConfiguration,<br>Set-AppvPublishingServer<br><br>**-CertFilterForClientSsl**<br>String  | Specifies the path to a valid certificate in the certificate store.  | Policy value not written (same as Not Configured) |
| Set-AppvClientConfiguration,<br>Set-AppvPublishingServer<br><br>**-VerifyCertificateRevocationList**<br>True (enabled); False (Disabled state)  | Verifies Server certificate revocation status before streaming with HTTPS.  | 0 |
| Set-AppvClientConfiguration,<br>Set-AppvPublishingServer<br><br>**-SharedContentStoreMode**<br>True (enabled); False (Disabled state)  | Specifies that streamed package contents will be not be saved to the local hard disk.  | 0 |
| Set-AppvPublishingServer<br><br>**-Name**<br>String  | Displays the name of publishing server.  | Policy value not written (same as Not Configured) |
| Set-AppvPublishingServer<br><br>**-URL**<br>String  | Displays the URL of publishing server.  | Policy value not written (same as Not Configured) |
| Set-AppvPublishingServer<br><br>**-GlobalRefreshEnabled**<br>True (enabled); False (Disabled state)  | Enables global publishing refresh (Boolean)  | False |
| Set-AppvPublishingServer<br><br>**-GlobalRefreshOnLogon**<br>True (enabled); False (Disabled state)  | Triggers a global publishing refresh on sign in. (Boolean)  | False |
| Set-AppvPublishingServer<br><br>**-GlobalRefreshInterval**<br>Integer (0–744)  | Specifies the publishing refresh interval using the GlobalRefreshIntervalUnit. To disable package refresh, specify 0.  | 0 |
| Set-AppvPublishingServer<br><br>**-GlobalRefreshIntervalUnit** <br>0 for hour, 1 for day  | Specifies the interval unit (Hour 0–23, Day 0–31).  | 1 |
| Set-AppvPublishingServer<br><br>**-UserRefreshEnabled**<br>True (enabled); False (Disabled state)  | Enables user publishing refresh (Boolean)  | False |
| Set-AppvPublishingServer<br><br>**-UserRefreshOnLogon**<br>True (enabled); False (Disabled state)  | Triggers a user publishing refresh on sign in. (Boolean) Word count (with spaces): 60  | False |
| Set-AppvPublishingServer<br><br>**-UserRefreshInterval**<br>Word count (with spaces): 85<br>Integer (0–744 Hours)  | Specifies the publishing refresh interval using the UserRefreshIntervalUnit. To disable package refresh, select 0.  | 0 |
| Set-AppvPublishingServer<br><br>**-UserRefreshIntervalUnit**<br>0 for hour, 1 for day  | Specifies the interval unit (Hour 0–23, Day 0–31).  | 1 |
| Set-AppvClientConfiguration,<br>Set-AppvPublishingServer<br><br>**-MigrationMode**<br>True (enabled state); False (Disabled state)  | Migration mode allows the App-V client to modify shortcuts and FTA’s for packages created by a previous version of App-V.  | |
| Set-AppvClientConfiguration,<br>Set-AppvPublishingServer<br><br>**-EnablePackageScripts**<br>True (enabled); False (Disabled state)  | Enables scripts defined in the package manifest of configuration files that should run.  | |
| Set-AppvClientConfiguration<br><br>**-RoamingFileExclusions**<br>String  | Specifies the file paths relative to %userprofile% that do not roam with a user's profile. For example, ```/ROAMINGFILEEXCLUSIONS='desktop;my pictures'```  | |
| Set-AppvClientConfiguration,<br>Set-AppvPublishingServer<br><br>**-RoamingRegistryExclusions**<br>String  | Specifies the registry paths that do not roam with a user profile. For example, ```/ROAMINGREGISTRYEXCLUSIONS=software\\classes;software\\clients```  | Policy value not written (same as Not Configured) |
| Set-AppvClientConfiguration,<br>Set-AppvPublishingServer<br><br>**-IntegrationRootUser**<br>String  | Specifies the location to create symbolic links associated with the current version of a per-user published package. All virtual application extensions, such as shortcuts and file type associations, will point to this path. If you don't specify a path, symbolic links will not be used when you publish the package. For example, ```%localappdata%\\Microsoft\\AppV\\Client\\Integration```.  | Policy value not written (same as Not Configured) |
| Set-AppvClientConfiguration,<br>Set-AppvPublishingServer<br><br>**-IntegrationRootGlobal**<br>String  | Specifies the location to create symbolic links associated with the current version of a globally published package. All virtual application extensions, such as shortcuts and file type associations, will point to this path. If you don't specify a path, symbolic links will not be used when you publish the package. For example, ```%allusersprofile%\\Microsoft\\AppV\\Client\\Integration```.  | Policy value not written (same as Not Configured) |
| Set-AppvClientConfiguration,<br>Set-AppvPublishingServer<br><br>**-VirtualizableExtensions**<br>String  | A comma-delineated list of file name extensions that can be used to determine if a locally installed application can be run in the virtual environment. When shortcuts, FTAs, and other extension points are created during publishing, App-V will compare the file name extension to the list if the application associated with the extension point is locally installed. If the extension is located, the **RunVirtual** command-line parameter will be added, and the application will run virtually. For more information about the **RunVirtual** parameter, see [Running a locally installed application inside a virtual environment with virtualized applications](appv-running-locally-installed-applications-inside-a-virtual-environment.md).  | Policy value not written |
| Set-AppvClientConfiguration,<br>Set-AppvPublishingServer<br><br>**-ReportingEnabled**<br>True (enabled); False (Disabled state)  | Returns information to a reporting server.  | False |
| Set-AppvClientConfiguration,<br>Set-AppvPublishingServer<br><br>**-ReportingServerURL**<br>String  | Specifies the location on the reporting server where client information is saved.  | Policy value not written (same as Not Configured) |
| Set-AppvClientConfiguration,<br>Set-AppvPublishingServer<br><br>**-ReportingDataCacheLimit**<br>Integer \[0–1024\]  | Specifies the maximum size in megabytes (MB) of the XML cache for storing reporting information. The size applies to the cache in memory. When the limit is reached, the log file will roll over. Set between 0 and 1024.  | Policy value not written (same as Not Configured) |
| Set-AppvClientConfiguration,<br>Set-AppvPublishingServer<br><br>**-ReportingDataBlockSize**<br>Integer \[1024 - Unlimited\]  | Specifies the maximum size in bytes to transmit to the server for reporting upload requests. This can help avoid permanent transmission failures when the log has reached a significant size. Set between 1024 and unlimited.  | Policy value not written (same as Not Configured) |
| Set-AppvClientConfiguration,<br>Set-AppvPublishingServer<br><br>**-ReportingStartTime**<br>Integer (0–23)  | Specifies the time to initiate the client to send data to the reporting server. You must specify a valid integer between 0–23 corresponding to the hour of the day. By default the **ReportingStartTime** will start on the current day at 10 P.M.or 22.<br>**Note** You should configure this setting to a time when computers running the App-V client are least likely to be offline.  | Policy value not written (same as Not Configured) |
| Set-AppvClientConfiguration,<br>Set-AppvPublishingServer<br><br>**-ReportingInterval**<br>Integer  | Specifies the retry interval that the client will use to resend data to the reporting server.  | Policy value not written (same as Not Configured) |
| Set-AppvClientConfiguration,<br>Set-AppvPublishingServer<br><br>**-ReportingRandomDelay**<br>Integer \[0 - ReportingRandomDelay\]  | Specifies the maximum delay (in minutes) for data to be sent to the reporting server. When the scheduled task is started, the client generates a random delay between 0 and **ReportingRandomDelay** and will wait the specified duration before sending data. This can help to prevent collisions on the server.  | Policy value not written (same as Not Configured) |
| Set-AppvClientConfiguration,<br>Set-AppvPublishingServer<br><br>**-EnableDynamicVirtualization<br>**1 (Enabled), 0 (Disabled)  | Enables supported Shell Extensions, Browser Helper Objects, and Active X controls to be virtualized and run with virtual applications.  | |
| Set-AppvClientConfiguration,<br>Set-AppvPublishingServer<br><br>**-EnablePublishingRefreshUI**<br>1 (Enabled), 0 (Disabled)  | Enables the publishing refresh progress bar for the computer running the App-V Client.  | |
| Sync-AppvPublishingServer<br><br>**-HidePublishingRefreshUI**<br>1 (Enabled), 0 (Disabled)  | Hides the publishing refresh progress bar.  | |
| Set-AppvClientConfiguration,<br>Set-AppvPublishingServer<br><br>**-ProcessesUsingVirtualComponents**<br>String  | Specifies a list of process paths (that may contain wildcards) that are candidates for using dynamic virtualization (such as supported shell extensions, browser helper objects, and ActiveX controls). Only processes whose full path matches one of these items can use dynamic virtualization.  | Empty string. |

## App-V client configuration settings: registry keys

The following table provides information about App-V client configuration settings that can be configured through the registry:

| **Setting name**<br>Type  | Registry key value  | Disabled policy state keys and values |
|---------------------------|---------------------|---------------------------------------|
| **PackageInstallationRoot**<br>String  | Streaming\\PackageInstallationRoot  | Policy value not written (same as Not Configured) |
| **PackageSourceRoot**<br>String  | Streaming\\PackageSourceRoot  | Policy value not written (same as Not Configured) |
| **AllowHighCostLaunch**<br>True (Enabled); False (Disabled state)  | Streaming\\AllowHighCostLaunch  | 0 |
| **ReestablishmentRetries**<br>Integer (0–99)  | Streaming\\ReestablishmentRetries  | Policy value not written (same as Not Configured) |
| **ReestablishmentInterval**<br>Integer (0–3600)  | Streaming\\ReestablishmentInterval  | Policy value not written (same as Not Configured) |
| **LocationProvider**<br>String  | Streaming\\LocationProvider  | Policy value not written (same as Not Configured) |
| **CertFilterForClientSsl**<br>String  | Streaming\\CertFilterForClientSsl  | Policy value not written (same as Not Configured) |
| **VerifyCertificateRevocationList**<br>True (Enabled); False (Disabled state)  | Streaming\\VerifyCertificateRevocationList  | 0 |
| **SharedContentStoreMode**<br>True (Enabled); False (Disabled state)  | Streaming\\SharedContentStoreMode  | 0 |
| **Name**<br>String  | Publishing\\Servers{serverId}\\FriendlyName  | Policy value not written (same as Not Configured) |
| **URL**<br>String  | Publishing\\Servers{serverId}\\URL  | Policy value not written (same as Not Configured) |
| **GlobalRefreshEnabled**<br>True (Enabled); False (Disabled state)  | Publishing\\Servers{serverId}\\GlobalEnabled  | False |
| **GlobalRefreshOnLogon**<br>True (Enabled); False (Disabled state)  | Publishing\\Servers{serverId}\\GlobalLogonRefresh  | False |
| **GlobalRefreshInterval**<br>Integer (0–744)  | Publishing\\Servers{serverId}\\GlobalPeriodicRefreshInterval  | 0 |
| **GlobalRefreshIntervalUnit** <br>0 for hour, 1 for day  | Publishing\\Servers{serverId}\\GlobalPeriodicRefreshIntervalUnit  | 1 |
| **UserRefreshEnabled**<br>True (Enabled); False (Disabled state)  | Publishing\\Servers{serverId}\\UserEnabled  | False |
| **UserRefreshOnLogon**<br>True (Enabled); False (Disabled state)  | Publishing\\Servers{serverId}\\UserLogonRefresh  | False |
| **UserRefreshInterval**<br>Word count (with spaces): 85; Integer (0–744 Hours)  | Publishing\\Servers{serverId}\\UserPeriodicRefreshInterval  | 0 |
| **UserRefreshIntervalUnit**<br>0 for hour, 1 for day  | Publishing\\Servers{serverId}\\UserPeriodicRefreshIntervalUnit  | 1 |
| **MigrationMode**<br>True(Enabled state); False (Disabled state)  | Coexistence\\MigrationMode  | |
| **EnablePackageScripts**<br>True (Enabled); False (Disabled state)  | \\Scripting\\EnablePackageScripts  | |
| **RoamingFileExclusions**<br>String  | | |
| **RoamingRegistryExclusions**<br>String  | Integration\\RoamingReglstryExclusions  | Policy value not written (same as Not Configured) |
| **IntegrationRootUser**<br>String  | Integration\\IntegrationRootUser  | Policy value not written (same as Not Configured) |
| **IntegrationRootGlobal**<br>String  | Integration\\IntegrationRootGlobal  | Policy value not written (same as Not Configured) |
| **VirtualizableExtensions**<br>String  | Integration\\VirtualizableExtensions  | Policy value not written |
| **ReportingEnabled**<br>True (Enabled); False (Disabled state)  | Reporting\\EnableReporting  | False |
| **ReportingServerURL**<br>String  | Reporting\\ReportingServer  | Policy value not written (same as Not Configured) |
| **ReportingDataCacheLimit**<br>Integer \[0–1024\]  | Reporting\\DataCacheLimit  | Policy value not written (same as Not Configured) |
| **ReportingDataBlockSize**<br>Integer \[1024–Unlimited\]  | Reporting\\DataBlockSize  | Policy value not written (same as Not Configured) |
| **ReportingStartTime**<br>Integer (0–23)  | Reporting\\ StartTime  | Policy value not written (same as Not Configured) |
| **ReportingInterval**<br>Integer  | Reporting\\RetryInterval  | Policy value not written (same as Not Configured) |
| **ReportingRandomDelay**<br>Integer \[0 - ReportingRandomDelay\]  | Reporting\\RandomDelay  | Policy value not written (same as Not Configured) |
| **EnableDynamicVirtualization<br>**1 (Enabled), 0 (Disabled)  | HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\AppV\\Client\\Virtualization  | |
| **EnablePublishingRefreshUI**<br>1 (Enabled), 0 (Disabled)  | HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\AppV\\Client\\Publishing  | |
| **HidePublishingRefreshUI**<br>1 (Enabled), 0 (Disabled)  | | |
| **ProcessesUsingVirtualComponents**<br>String  | Virtualization\\ProcessesUsingVirtualComponents  | Empty string. |





## Related topics

* [Deploying the App-V Sequencer and Configuring the Client](appv-deploying-the-appv-sequencer-and-client.md)
