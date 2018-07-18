---
title: Unity のログ コールバックを VSTU と共有する | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 31fa20bd4fd5a28e705198f9112e309e627871cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31060006"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Unity のログ コールバックを VSTU と共有する
Visual Studio Tools for Unity では、Unity コンソールを Visual Studio にストリーミングできるよう、Unity にログ コールバックを登録します。 エディターのスクリプトもログ コールバックを Unity に登録すると、そのコールバックが VSTU コールバックから影響を受けることがあります。 この可能性を回避するには、`VisualStudioIntegration.LogCallback` イベントを使用して VSTU と連携します。

## <a name="demonstrates"></a>使用例
 Visual Studio Tools for Unity によって作成されるログ コールバックを共有する方法を示します。

## <a name="example"></a>例

```csharp
using System;

using UnityEngine;
using UnityEditor;

using SyntaxTree.VisualStudio.Unity.Bridge;

[InitializeOnLoad]
public class LogCallbackHook
{
    static LogCallbackHook()
    {
        VisualStudioIntegration.LogCallback += (string condition, string trace, LogType type) =>
        {
            // place code that implements your log callback here
        };
    }
}
```

## <a name="see-also"></a>参照
 [例: プロジェクト ファイルの生成](../cross-platform/customize-project-files-created-by-vstu.md)
