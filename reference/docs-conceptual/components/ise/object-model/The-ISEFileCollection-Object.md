---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISEFileCollection 对象
ms.openlocfilehash: 96db51ee921cc0fa34803091d563bc6e118643b6
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030515"
---
# <a name="the-isefilecollection-object"></a>ISEFileCollection 对象

**ISEFileCollection** 对象是 **ISEFile** 对象的集合。 例如，$psISE.CurrentPowerShellTab.Files 集合。

## <a name="methods"></a>方法

### <a name="add-fullpath-"></a>Add\( \[fullPath\] \)

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

创建并返回一个新的未命名文件，并将其添加到集合中。 新创建的文件的 **IsUntitled** 属性为 **$true**。

**\[fullPath\]** - 可选字符串，表示文件的完全指定路径。 如果包含 **fullPath** 参数和相对路径，或者如果你使用文件名而不是完整路径，则会生成异常。

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a>Remove\( File, \[Force\] \)

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

从当前 PowerShell 选项卡中删除指定的文件。

**File** - 字符串，表示要从集合中删除的 ISEFile 文件。 如果尚未保存该文件，此方法将引发异常。 使用 **Force** 开关参数强制删除未保存的文件。

**\[Force\]** - 可选布尔值，如果设置为 **$true**，即使在最后一次使用后尚未保存文件，也会授予权限来删除该文件。 默认值为 **$false**。

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a>SetSelectedFile\( selectedFile \)

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

选择由 **selectedFile** 参数指定的文件。

**selectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile，要选择的 ISEFile 文件。

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a>另请参阅

- [ISEFile 对象](The-ISEFile-Object.md)
- [Windows PowerShell ISE 脚本对象模型的用途](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 对象模型层次结构](The-ISE-Object-Model-Hierarchy.md)
