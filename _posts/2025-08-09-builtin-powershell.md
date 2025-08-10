---
title: "Built-in_Functions in powershell"
date: 2025-08-09
tags: [powershell]
author: "Romain Dehasseleer"
---

---

### Built-in_Functions in powershell

List of built-in functions in powershell to remember.

```powershell
Test-NetConnection "hostname|ip" -Port 3690
```

Date formatting

```powershell
Get-Date -Format "yyyyMMdd"
```

Web requests

```powershell
Invoke-RestMethod -Uri <url> -Method Get
Invoke-WebRequest -Uri <url> -Method Post
```

Json conversion
```powershell
"command" | ConvertTo-Json -Depth 10 | Set-Content -Encoding utf8 -Path $outputFile
"command" | ConvertFrom-Json
```

CSV output
```powershell
"command" | ConvertTo-Csv | Out-File -Encoding UTF8 -FilePath "file.csv"
```

Proxy setup
```powershell

$proxy_url = "proxy_url"
$proxy = New-Object System.Net.WebProxy($proxy_url)
$proxy.Credentials = [System.Net.CredentialCache]::DefaultNetworkCredentials

$session = New-Object Microsoft.PowerShell.Commands.WebRequestSession
$session.Proxy = $proxy
$response = Invoke-WebRequest -UseBasicParsing -Uri "url" -Method POST -WebSession $session ...
```

Out-File
```powershell
<command> | Set-Content -Encoding utf8 -Path $outputFile
```

Array
```powershell
$ids = @{
    mons="28196"
    nivelles="27235"
    namur="30014"
    luxembourg="228714"
}
foreach ($id in $ids.Keys){
    ...
}
```

Join string
```powershell
  $name_archive = -join($dateStart,"_",$endDate,"",".zip");
```