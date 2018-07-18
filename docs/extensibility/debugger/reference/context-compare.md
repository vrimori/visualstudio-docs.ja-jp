---
title: CONTEXT_COMPARE |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0563f037f77c18cc5e686c1ea6acf429c91ad06d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108584"
---
# <a name="contextcompare"></a>CONTEXT_COMPARE
2 つのメモリ コンテキストを比較するための条件を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
typedef DWORD CONTEXT_COMPARE;  
```  
  
```csharp  
public enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
```  
  
## <a name="members"></a>メンバー  
 CONTEXT_EQUAL  
 ターゲット メモリ コンテキストに相当するリスト内の最初のメモリ コンテキストを求めます。  
  
 CONTEXT_LESS_THAN  
 ターゲット メモリ コンテキストよりも小さいリスト内の最初のメモリ コンテキストを求めます。  
  
 CONTEXT_GREATER_THAN  
 ターゲット メモリ コンテキストよりも大きいリスト内の最初のメモリ コンテキストを求めます。  
  
 CONTEXT_LESS_THAN_OR_EQUAL  
 以下をターゲット メモリ コンテキストには、一覧に最初のメモリ コンテキストを検索します。  
  
 CONTEXT_GREATER_THAN_OR_EQUAL  
 大きいかメモリのターゲット コンテキストを等しい値をリスト内の最初のメモリ コンテキストを求めます。  
  
 CONTEXT_SAME_SCOPE  
 メモリのターゲット コンテキストと同じスコープ内にある一覧で最初のメモリ コンテキストを検索します。  
  
 CONTEXT_SAME_FUNCTION  
 ターゲット メモリの範囲と同じ関数内にあるリストの最初のメモリ コンテキストを検索します。  
  
 CONTEXT_SAME_MODULE  
 メモリのターゲット コンテキストと同じモジュールであるリストの最初のメモリ コンテキストを検索します。  
  
 CONTEXT_SAME_PROCESS  
 メモリのターゲット コンテキストと同じプロセス内にある一覧で最初のメモリ コンテキストを検索します。  
  
## <a name="remarks"></a>コメント  
 引数として渡される、[比較](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)メソッドです。  
  
 これらの値は、指定した比較条件を満たすリスト内の最初のメモリ コンテキストの検索に使用されます。 メモリ コンテキストを通じて自体に対して比較するメモリ コンテキストの一覧を指定、`IDebugMemoryContext2::Compare`メソッドです。 比較演算子の一覧の最初のメモリ コンテキスト`true`次が返されます。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)