---
title: BP_COND_STYLE |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ea5e0df33ef462d6b1b8bbe013f30baab894ea82
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535277"
---
# <a name="bpcondstyle"></a>BP_COND_STYLE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[BP_COND_STYLE](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/bp-cond-style)します。  
  
保留中のブレークポイントの条件のスタイルを指定し、ブレークポイントをバインドします。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
typedef DWORD BP_COND_STYLE;  
```  
  
```csharp  
public enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
```  
  
## <a name="members"></a>メンバー  
 BP_COND_NONE  
 ブレークポイントの位置に達すると、ブレークポイントが発生します。 ブレークポイントの条件を指定します。  
  
 BP_COND_WHEN_TRUE  
 評価される条件式がブレークポイントに関連付けられている場合のみ、ブレークポイントを発生させる`true`します。  
  
 BP_COND_WHEN_CHANGED  
 条件付きの式の値は、ブレークポイントに関連付けられている場合にのみ、ブレークポイントがその以前の評価から変更が発生します。  
  
## <a name="remarks"></a>Remarks  
 使用、`styleCondition`のメンバー、 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)構造体。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)

