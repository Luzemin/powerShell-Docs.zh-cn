---
title: Runspace02 （C#）代码示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59a7b8b9-f72e-43fd-9a10-77404441a3f2
caps.latest.revision: 6
ms.openlocfilehash: abf539bc29bd9ccac59bd5957397fbe68951f266
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366616"
---
# <a name="runspace02-c-code-sample"></a>Runspace02 (C#) 代码示例

下面是 Runspace02 C#示例的源代码。 此示例使用[Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke)类来同步执行 `Get-Process` cmdlet。 然后，使用 Windows 窗体和数据绑定在 DataGridView 控件中显示结果

## <a name="code-sample"></a>代码示例

[!code-csharp[Runspace02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace02/Runspace02.cs#L11-L82 "Runspace02.cs")]

## <a name="see-also"></a>另请参阅

[Windows PowerShell SDK](../windows-powershell-reference.md)
