---
title: CONTEXT_COMPARE |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d43e50addf590dabcfcc8e3661d27546881452cb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51770305"
---
# <a name="contextcompare"></a>CONTEXT_COMPARE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

メモリの 2 つのコンテキストを比較するための条件を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
enum enum_CONTEXT_COMPARE {   
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
public enum enum_CONTEXT_COMPARE {   
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
 ターゲット メモリのコンテキストに相当するリスト内の最初のメモリのコンテキストを検索します。  
  
 CONTEXT_LESS_THAN  
 ターゲット メモリのコンテキストよりも小さいリスト内の最初のメモリのコンテキストを検索します。  
  
 CONTEXT_GREATER_THAN  
 ターゲット メモリのコンテキストよりも大きいリスト内の最初のメモリのコンテキストを検索します。  
  
 CONTEXT_LESS_THAN_OR_EQUAL  
 ターゲット メモリ コンテキスト以下であるリストで最初のメモリのコンテキストを検索します。  
  
 CONTEXT_GREATER_THAN_OR_EQUAL  
 ターゲット メモリ コンテキスト以上であるリストで最初のメモリのコンテキストを検索します。  
  
 CONTEXT_SAME_SCOPE  
 ターゲット メモリのコンテキストと同じスコープ内にある一覧で最初のメモリのコンテキストを検索します。  
  
 CONTEXT_SAME_FUNCTION  
 ターゲット メモリのスコープと同じ機能であるリストで最初のメモリのコンテキストを検索します。  
  
 CONTEXT_SAME_MODULE  
 ターゲット メモリのコンテキストと同じモジュール内にある一覧で最初のメモリのコンテキストを検索します。  
  
 CONTEXT_SAME_PROCESS  
 ターゲット メモリのコンテキストと同じプロセス内にある一覧で最初のメモリのコンテキストを検索します。  
  
## <a name="remarks"></a>Remarks  
 引数として渡される、[比較](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)メソッド。  
  
 これらの値は、指定した比較条件を満たすリスト内の最初のメモリのコンテキストの検索に使用されます。 メモリ コンテキストがを介してに対して自身を比較するメモリのコンテキストの一覧を指定された、`IDebugMemoryContext2::Compare`メソッド。 比較演算子の一覧で最初のメモリ コンテキスト`true`が返されます。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)

