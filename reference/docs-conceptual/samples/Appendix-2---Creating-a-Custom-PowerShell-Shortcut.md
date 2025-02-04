---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 附录 2 - 创建自定义 PowerShell 快捷方式
ms.openlocfilehash: 6f1a6a8187b1797103e3620b2cf9155978807ea5
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030301"
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a>附录 2 - 创建自定义 PowerShell 快捷方式

下面的过程描述如何创建对多个方便的选项进行了自定义的 Windows PowerShell 快捷方式。

1. 创建指向 Powershell.exe 的快捷方式。

2. 右键单击该快捷方式，然后单击“**属性**”。

3. 单击“选项”选项卡。

4. 在“编辑选项”部分中，选中“QuickEdit”复选框。

    此设置让你能够通过拖动鼠标左键在 Windows PowerShell 控制台窗口中选择文本，它还允许你通过按 ENTER 或右键单击鼠标将文本复制到剪贴板。

5. 在“编辑选项”部分中，选中“插入模式”复选框。 此设置让你能够通过在控制台窗口中右键单击来自动粘贴剪贴板中的文本。

6. 在“命令历史记录”部分中，在“缓冲区大小”框中键入或选择一个介于 1 和 999 之间的数字。 这将设置要保存在控制台缓冲区中的已键入命令数。

7. 在“命令历史记录”部分中，选中“丢弃旧的副本”复选框以清除控制台缓存区中的重复命令。

8. 单击“布局”选项卡。

9. 在“屏幕缓冲区”部分中，在“高度”框中键入一个介于 1 和 9999 之间的数字。 该高度表示已缓冲输出的行数。 这是滚过控制台窗口时可查看的最大保留行数。 如果此数字小于“窗口大小”部分中所示的高度，窗口大小高度将自动降低为相同的值。

10. 在“窗口大小”部分中，键入一个介于 1 和 9999 之间的数字用作宽度。 这表示在控制台窗口中横向显示的字符数。 默认宽度为 80，Windows PowerShell 的输出格式就是针对此宽度而设计。

11. 如果你想要在控制台打开时将它放置在桌面上的某个特定点上，请清除“窗口位置”部分中的“由系统定位窗口”复选框，然后更改“窗口位置”部分中“左侧”和“顶部”框中的值。

12. 单击**确定**。
