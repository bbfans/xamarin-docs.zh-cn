---
title: Xamarin.Essentials 剪贴板
description: 剪贴板类允许您复制并粘贴到系统剪贴板应用程序之间的文本。
ms.assetid: C52AE99A-0FB3-425D-9106-3DA5777FEFA0
author: jamesmontemagno
ms.author: jamont
ms.date: 05/04/2018
ms.openlocfilehash: 67a0218325918b57e5ed2618b57d52d3fe3ee820
ms.sourcegitcommit: 3e05b135b6ff0d607bc2378c1b6e66d2eebbcc3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/12/2018
---
# <a name="xamarinessentials-clipboard"></a>Xamarin.Essentials 剪贴板

![预发行 NuGet](~/media/shared/pre-release.png)

**剪贴板**类可复制并粘贴到系统剪贴板应用程序之间的文本。

## <a name="using-clipboard"></a>使用剪贴板

在你的类中添加对 Xamarin.Essentials 的引用：

```csharp
using Xamarin.Essentials;
```

若要检查**剪贴板**具有当前准备要粘贴的文本：

```csharp
var hasText = Clipboard.HasText;
```

将文本设置为**剪贴板**:

```csharp
ClipBoard.SetText("Hello World");
```

若要读取从文本**剪贴板**:

```csharp
var text = await Clipboard.GetTextAsync();
```

## <a name="api"></a>API

- [剪贴板源代码](https://github.com/xamarin/Essentials/tree/master/Xamarin.Essentials/Clipboard)
- [剪贴板 API 文档](xref:Xamarin.Essentials.Clipboard)
