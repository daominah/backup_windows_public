# AssetStudio Download

## Fork (2025-09)

<https://github.com/aelurum/AssetStudio>

## Original (archived)

<https://github.com/Perfare/AssetStudio/releases>

Latest release v0.16.47 (2022-06-16):
<https://github.com/Perfare/AssetStudio/releases/download/v0.16.47/AssetStudio.net472.v0.16.47.zip>

## Check .NET version

```powershell
Get-ChildItem "HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP" -Recurse |
  Get-ItemProperty -Name Version -ErrorAction SilentlyContinue |
  Select-Object PSChildName, Version
```

Output (likely v4.x):

```
PSChildName Version
----------- -------
Client      4.8.09037
1033        4.8.09037
Full        4.8.09037
1033        4.8.09037
Client      4.0.0.0
```
