# LocalAIWorkspace Windows x64

这是 `LocalAIWorkspace-win-x64.zip` 的 GitHub Release 分卷下载页。

## 下载与合并

请在 Releases 页面下载全部 `LocalAIWorkspace-win-x64.zip.part01` 至最后一个分卷，并放在同一目录。

PowerShell 合并命令：

```powershell
$parts = Get-ChildItem .\LocalAIWorkspace-win-x64.zip.part* | Sort-Object Name
$out = [IO.File]::OpenWrite('.\LocalAIWorkspace-win-x64.zip')
try {
    foreach ($part in $parts) {
        $in = [IO.File]::OpenRead($part.FullName)
        try { $in.CopyTo($out) } finally { $in.Dispose() }
    }
} finally { $out.Dispose() }
```

合并后请使用 Release 页面记录的 SHA-256 校验值验证原始 ZIP，再解压运行。

本文件没有写入 Git 历史，模型和运行时只作为 Release 资产保存。
