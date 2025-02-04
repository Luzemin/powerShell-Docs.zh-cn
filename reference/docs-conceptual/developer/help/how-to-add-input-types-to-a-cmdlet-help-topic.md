---
title: 如何向 Cmdlet 帮助主题添加输入类型 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: f213605dda0132051d983f8608515325e815c455
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361236"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>如何向 Cmdlet 帮助主题添加输入类型

本部分介绍如何将输入部分添加到 Windows PowerShell® cmdlet 帮助主题。 "输入" 部分列出了 cmdlet 作为管道的输入接受的对象的 .NET 类，可以通过值或按属性名称。

可以添加到输入部分的类的数量没有限制。 输入类型括在 \<command： inputTypes > 节点中，其中每个类都包含在 \<command： inputType > 元素中。

此架构包括两个 \<maml： description > 每个 \<command： inputType > 元素中的元素。 但 @no__t cmdlet 只显示 @no__t 1command： inputType >/\<maml： description >）元素的内容。

从 Windows PowerShell 3.0 开始，@no__t cmdlet 显示 \<maml： uri > 元素的内容。 此元素使用户能够将用户定向到描述 .NET 类的主题。

下面的 XML 显示 \<maml： inputTypes > 节点。

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> Class name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Brief description </maml:para>
    </maml:description>
  </command:inputType>
</command:inputTypes>
```

下面的 XML 显示使用 \<maml： inputTypes > 节点记录输入类型的示例。

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```