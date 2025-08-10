---
title: "Folder size in powershell"
date: 2025-08-09
tags: [powershell]
author: "Romain Dehasseleer"
---

---

### Folder size in powershell

How can you see how much space you’re wasting on Windows?  
No, I’m not deleting your 8-year-old Final_v3_really_final.docx for you.

```powershell
function Get-FolderTreeWithSizes {
    param (
        [string]$Path,
        [int]$Indent = 0
    )

    $items = Get-ChildItem -Path $Path -Force
    $folderSize = 0

    foreach ($item in $items) {
        if ($item.PSIsContainer) {
            $subFolderSize = (Get-ChildItem -Path $item.FullName -Recurse -Force | Measure-Object -Property Length -Sum).Sum
            $subFolderSizeKB = "{0:N2} KB" -f ($subFolderSize / 1KB)
            Write-Host (" " * $Indent + "+-- " + $item.Name + " [Folder] (" + $subFolderSizeKB + ")") -ForegroundColor Green
            Get-FolderTreeWithSizes -Path $item.FullName -Indent ($Indent + 4)
        } else {
            $fileSizeKB = "{0:N2} KB" -f ($item.Length / 1KB)
            Write-Host (" " * $Indent + "+-- " + $item.Name + " (" + $fileSizeKB + ")") -ForegroundColor Yellow
            $folderSize += $item.Length
        }
    }

    if ($Indent -eq 0) {
        Write-Host ("Total Size of '$Path': {0:N2} MB" -f ($folderSize / 1MB)) -ForegroundColor Cyan
    }
}

 
Get-FolderTreeWithSizes "C:\folder\to\check"
```
No, I’m not deleting my 8-year-old Final_final_really_final_v3.docx.
