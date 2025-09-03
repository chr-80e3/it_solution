# 使用 PowerShell 列出所有软件并保存到文件

这篇文章将指导你如何使用 **PowerShell** 列出电脑上所有已安装的软件，包括传统的桌面程序和微软商店（Microsoft Store）应用，并将列表保存为一个文本文件，方便备份和查看。

## 为什么选择 PowerShell？

与通过“程序和功能”手动截图或记录不同，使用 PowerShell 自动化这个过程更加高效和准确。它能一次性获取所有信息，并以文本格式保存，方便你日后搜索或导入。

## 操作步骤

1.  **打开 PowerShell**：
    在 Windows 开始菜单中搜索 `"PowerShell"`，然后右键点击，选择 `"以管理员身份运行"`。

2.  **执行命令**：
    将以下两条命令按顺序复制并粘贴到 PowerShell 窗口中，然后按回车键执行。

    -   **第一条命令（获取传统桌面程序）**：
        ```powershell
        Get-ItemProperty HKLM:\Software\Wow6432Node\Microsoft\Windows\CurrentVersion\Uninstall\*, HKLM:\Software\Microsoft\Windows\CurrentVersion\Uninstall\* | Select-Object DisplayName | Sort-Object DisplayName | Out-File -FilePath "$env:USERPROFILE\Desktop\Installed_Software_List.txt" -Encoding UTF8
        ```
        这条命令会搜索 Windows 注册表，找出所有传统的桌面应用程序，并将它们的名称按字母顺序排列。

    -   **第二条命令（追加微软商店应用）**：
        ```powershell
        Get-AppxPackage | Select-Object Name | Sort-Object Name | Out-File -FilePath "$env:USERPROFILE\Desktop\Installed_Software_List.txt" -Append -Encoding UTF8
        ```
        这条命令会获取所有通过微软商店安装的应用程序，将其名称按字母顺序排列，然后 **追加** 到上一步创建的文本文件的末尾。

## 命令详解

-   **`Get-ItemProperty ...`**：获取已安装的传统桌面应用信息。
-   **`Get-AppxPackage`**：获取微软商店应用包的信息。
-   **`Select-Object DisplayName` / `Select-Object Name`**：只提取软件的名称。
-   **`Sort-Object`**：对获取到的软件名称进行排序。
-   **`Out-File`**：将输出结果保存到文件。
-   **`-FilePath "$env:USERPROFILE\Desktop\Installed_Software_List.txt"`**：指定文件保存的路径和名称。`$env:USERPROFILE\Desktop\` 是你的桌面文件夹。
-   **`-Append`**：这个参数是关键，它确保第二条命令的输出是 **追加** 到文件末尾，而不是覆盖。
-   **`-Encoding UTF8`**：指定文件编码为 UTF-8，以确保中文字符显示正常。

## 导出文件后的操作

命令运行完毕后，你的桌面上会生成一个名为 `Installed_Software_List.txt` 的文本文件。你可以打开它，查看你电脑上所有已安装的软件列表。

你可以将这个文件备份到云端或外部存储设备，作为你日后重装系统或在新电脑上恢复软件时的参考。
