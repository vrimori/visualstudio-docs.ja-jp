---
title: DOCCONTEXT_COMPARE |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 966d31889d7979732af20f5e3f95546e87af6598
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103654"
---
# <a name="doccontextcompare"></a>DOCCONTEXT_COMPARE
2 つのドキュメントのコンテキストを比較するための条件を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
typedef DWORD DOCCONTEXT_COMPARE;  
```  
  
```csharp  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
```  
  
## <a name="members"></a>メンバー  
 DOCCONTEXT_EQUAL  
 ターゲット ドキュメントのコンテキストに相当するリスト内の最初のドキュメントのコンテキストを求めます。  
  
 DOCCONTEXT_LESS_THAN  
 ターゲット ドキュメントのコンテキストよりも小さいリスト内の最初のドキュメントのコンテキストを求めます。  
  
 DOCCONTEXT_GREATER_THAN  
 ターゲット ドキュメントのコンテキストよりも大きいリスト内の最初のドキュメントのコンテキストを求めます。  
  
 DOCCONTEXT_SAME_DOCUMENT  
 ターゲット ドキュメントのコンテキストと同じドキュメント内にある一覧では、最初のドキュメントのコンテキストを検索します。  
  
## <a name="remarks"></a>コメント  
 引数として渡される、[比較](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)メソッドです。  
  
 これらの値は、リストの最初のドキュメントのコンテキストを検索するための比較条件の指定に使用されます。 ドキュメントのコンテキストがを通じて自体に対して比較するドキュメント コンテキストの一覧を指定された、`IDebugDocumentContext2::Compare`メソッドです。 比較演算子の一覧の最初のドキュメントのコンテキスト`true`次が返されます。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)