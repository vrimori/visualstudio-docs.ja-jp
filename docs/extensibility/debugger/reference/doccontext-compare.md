---
title: "DOCCONTEXT_COMPARE | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DOCCONTEXT_COMPARE"
helpviewer_keywords: 
  - "DOCCONTEXT_COMPARE 列挙型"
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# DOCCONTEXT_COMPARE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

2 種類のコンテキストを比較するための条件を指定します。  
  
## 構文  
  
```cpp#  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
typedef DWORD DOCCONTEXT_COMPARE;  
```  
  
```c#  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
```  
  
## メンバー  
 DOCCONTEXT\_EQUAL  
 対象のドキュメントのコンテキストと同じリストの最初のドキュメントのコンテキストを探します。  
  
 DOCCONTEXT\_LESS\_THAN  
 で対象のドキュメントのコンテキストより小さいリストの最初のドキュメントのコンテキストを探します。  
  
 DOCCONTEXT\_GREATER\_THAN  
 対象のドキュメントのコンテキストより大きなリストの最初のドキュメントのコンテキストを探します。  
  
 DOCCONTEXT\_SAME\_DOCUMENT  
 対象のドキュメントのコンテキスト同じドキュメントにあるリストの最初のドキュメントのコンテキストを探します。  
  
## 解説  
 [比較](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) のメソッドに引数として渡されます。  
  
 リストに値が最初のドキュメントのコンテキストを確認するには比較条件を指定するために使用されます。  ドキュメントのコンテキストは `IDebugDocumentContext2::Compare` のメソッドによってに対して自身を比較するためのコンテキストの一覧を示します。  比較演算子を `true` なリストの最初のドキュメントのコンテキストはを返します。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [比較](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)