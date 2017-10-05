---
title: "DOCCONTEXT_COMPARE |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 77c810bb6e4791fbc0c3cf787f340a8d996ce037
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

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
