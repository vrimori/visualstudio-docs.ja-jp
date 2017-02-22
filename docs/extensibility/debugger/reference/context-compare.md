---
title: "CONTEXT_COMPARE | Microsoft Docs"
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
  - "CONTEXT_COMPARE"
helpviewer_keywords: 
  - "CONTEXT_COMPARE 列挙型"
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# CONTEXT_COMPARE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

2 個のメモリのコンテキストを比較するための条件を指定します。  
  
## 構文  
  
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
  
```c#  
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
  
## メンバー  
 CONTEXT\_EQUAL  
 ターゲットのメモリのコンテキストと同じリストの最初のメモリのコンテキストを探します。  
  
 CONTEXT\_LESS\_THAN  
 ターゲットであるメモリのコンテキストより小さいリストの最初のメモリのコンテキストを探します。  
  
 CONTEXT\_GREATER\_THAN  
 ターゲットのメモリのコンテキストより大きなリストの最初のメモリのコンテキストを探します。  
  
 CONTEXT\_LESS\_THAN\_OR\_EQUAL  
 ターゲットのメモリのコンテキスト以下であるリストの最初のメモリのコンテキストを探します。  
  
 CONTEXT\_GREATER\_THAN\_OR\_EQUAL  
 より大きい \[ターゲットのメモリのコンテキストに設定します。リストの最初のメモリをコンテキスト。  
  
 CONTEXT\_SAME\_SCOPE  
 ターゲットのメモリのコンテキストと同じスコープ内にあるリストの最初のメモリのコンテキストを探します。  
  
 CONTEXT\_SAME\_FUNCTION  
 ターゲットのメモリの範囲と同じ機能にあるリストの最初のメモリのコンテキストを探します。  
  
 CONTEXT\_SAME\_MODULE  
 ターゲットのメモリのコンテキストと同じモジュールにあるリストの最初のメモリのコンテキストを探します。  
  
 CONTEXT\_SAME\_PROCESS  
 ターゲットのメモリのコンテキストと同じプロセスにあるリストの最初のメモリのコンテキストを探します。  
  
## 解説  
 [比較](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) のメソッドに引数として渡されます。  
  
 これらの値は指定した比較条件を満たすリスト内の最初のメモリのコンテキストを検索するために使用されます。  メモリの `IDebugMemoryContext2::Compare` のコンテキストがメソッドを介してに対して自身を比較するメモリのコンテキストの一覧を示します。  比較演算子を `true` なリストに対するメモリの最初のコンテキストはを返します。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [比較](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)