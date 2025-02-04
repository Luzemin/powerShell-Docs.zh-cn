---
title: Runspace06 示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 471c85f3-9287-45c2-b4bc-833caa1b7634
caps.latest.revision: 8
ms.openlocfilehash: 3850aec88bc800718a82f51c91fbd0cb3c705089
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367586"
---
# <a name="runspace06-sample"></a>Runspace06 示例

此示例演示如何将模块添加到[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象中，以便在打开运行空间时加载该模块。 该模块提供了一个通过使用[GetProcessSample02 示例](../cmdlet/getprocesssample02-sample.md)来同步运行的获取处理器 cmdlet （由该示例定义） [。](/dotnet/api/system.management.automation.powershell)

## <a name="requirements"></a>要求

此示例需要 Windows PowerShell 2.0。

## <a name="demonstrates"></a>示例

此示例演示以下各项。

- 正在创建一个[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象。

- 将该模块添加到[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象中。

- 使用[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象创建一个使用的 system.servicemodel. e i.[管理](/dotnet/api/System.Management.Automation.Runspaces.Runspace)对象。

- 创建使用运行空间的[system.web](/dotnet/api/system.management.automation.powershell)对象。

- 将模块的进程 cmdlet 添加到[系统管理](/dotnet/api/system.management.automation.powershell)对象的管道。

- 同步运行命令。

- 从命令返回的[system.object](/dotnet/api/System.Management.Automation.PSObject)对象中提取属性。

## <a name="example"></a>示例

此示例将创建一个运行空间，该运行空间使用[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象来定义打开运行空间时可用的元素。 在此示例中，将定义一个过程 cmdlet 的模块添加到初始会话状态。

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace06
  {
    /// <summary>
    /// This sample shows how to define an initial session state that is
    /// used when creating a runspace. The sample invokes a command from
    /// a binary module that is loaded by the initial session state.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample assumes that user has coppied the GetProcessSample02.dll
    /// that is produced by the GetProcessSample02 sample to the current
    /// directory.
    /// This sample demonstrates the following:
    /// 1. Creating a default initial session state.
    /// 2. Adding a module to the initial session state.
    /// 3. Creating a runspace that uses the initial session state.
    /// 4. Creating a PowerShell object that uses the runspace.
    /// 5. Adding the module's get-proc cmdlet to the PowerShell object.
    /// 6. Running the command synchronously.
    /// 7. Using PSObject objects to extract and display properties from
    ///    the objects returned by the cmdlet.
    /// </remarks>
    private static void Main(string[] args)
    {
        // Create the default initial session state and add the module.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      iss.ImportPSModule(new string[] { @".\GetProcessSample02.dll" });

      // Create a runspace. Notice that no PSHost object is supplied to the
      // CreateRunspace method so the default host is used. See the Host
      // samples for more information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        // Create a PowerShell object.
        using (PowerShell powershell = PowerShell.Create())
        {
          // Add the cmdlet and specify the runspace.
          powershell.AddCommand(@"GetProcessSample02\get-proc");
          powershell.Runspace = myRunSpace;

          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Process              HandleCount");
          Console.WriteLine("--------------------------------");

          // Display the results.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                              "{0,-20} {1}",
                              result.Members["ProcessName"].Value,
                              result.Members["HandleCount"].Value);
          }
        }

        // Close the runspace to release any resources.
        myRunSpace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 主机应用程序](./writing-a-windows-powershell-host-application.md)