---
title: Unity のログ コールバックを VSTU と共有する | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
caps.latest.revision: 5
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 9e309f7d7340eb73de587c7a5f569377354dbab9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186863"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Unity のログ コールバックを VSTU と共有する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
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
  
## <a name="see-also"></a>関連項目  
 [例: プロジェクト ファイルの生成](../cross-platform/customize-project-files-created-by-vstu.md)

