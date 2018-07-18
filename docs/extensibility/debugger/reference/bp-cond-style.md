---
title: BP_COND_STYLE |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 64c3ac876f0d7be8582ca8162fd93c83cb6d343e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100895"
---
# <a name="bpcondstyle"></a>BP_COND_STYLE
保留中のブレークポイントの条件のスタイルを指定し、ブレークポイントをバインドします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
 ブレークポイントの位置に達したときに、ブレークポイントが発生します。 ブレークポイントの条件を指定します。  
  
 BP_COND_WHEN_TRUE  
 評価条件式が、ブレークポイントに関連付けられている場合のみ、ブレークポイントを発生させる`true`です。  
  
 BP_COND_WHEN_CHANGED  
 発生条件式の値は、ブレークポイントに関連付けられている場合にのみ、ブレークポイントは、その以前の評価から変更されました。  
  
## <a name="remarks"></a>コメント  
 使用、`styleCondition`のメンバー、 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)構造体。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)