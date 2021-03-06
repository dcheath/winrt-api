---
-api-id: T:Windows.ApplicationModel.PackageCatalog
-api-type: winrt class
---

<!-- Class syntax.
public class PackageCatalog : Windows.ApplicationModel.IPackageCatalog, Windows.ApplicationModel.IPackageCatalog2
-->

# Windows.ApplicationModel.PackageCatalog

## -description
Provides access to app packages on the device.

## -remarks
Note that for PackageCatalog events:   

- If the PackageCatalog object is obtained using **[OpenForCurrentUser](https://docs.microsoft.com/uwp/api/windows.applicationmodel.packagecatalog#Windows_ApplicationModel_PackageCatalog_OpenForCurrentUser)**, package events will be received for all packages being installed for the current user.  

- If the PackageCatalog object is obtained using **[OpenForCurrentPackage](https://docs.microsoft.com/uwp/api/windows.applicationmodel.packagecatalog#Windows_ApplicationModel_PackageCatalog_OpenForCurrentPackage)**, package events will be received for the current package or its related packages such as optional packages.  

## -examples

## -see-also
[Package.Dependencies](package_dependencies.md)  