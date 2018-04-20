---
title: Win10彻底移除OneDrive
date: 2017-11-06
tag:
  - Win10
  - OneDrive
category: Windows
---

```bat
@REM kill process
taskkill /f /im OneDrive.exe

@REM uninstall(64bit system)
%SystemRoot%\SysWOW64\OneDriveSetup.exe /uninstall

@REM uninstall(32bit system)
@REM %SystemRoot%\System32\OneDriveSetup.exe /uninstall

@REM Delete folder
rd "%UserProfile%\OneDrive" /Q /S
rd "%LocalAppData%\Microsoft\OneDrive" /Q /S
rd "%ProgramData%\Microsoft OneDrive" /Q /S
rd "C:\OneDriveTemp" /Q /S

@REM Remove Quick access
REG Delete "HKEY_CLASSES_ROOT\CLSID\{018D5C66-4533-4307-9B53-224DE2ED1FE6}" /f

@pause
```