---
title: "BP_LOCATION_DATA_STRING | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION_DATA_STRING"
helpviewer_keywords: 
  - "BP_LOCATION_DATA_STRING 構造体"
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_LOCATION_DATA_STRING
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

統合開発環境からユーザーが入力できる文字列に基づいてデータ ブレークポイントを設定する場合に使用 \(IDE\) します。  
  
## 構文  
  
```cpp#  
typedef struct _BP_LOCATION_DATA_STRING {   
   IDebugThread2* pThread;  
   BSTR           bstrContext;  
   BSTR           bstrDataExpr;  
   DWORD          dwNumElements;  
} BP_LOCATION_DATA_STRING;  
```  
  
## メンバー  
 `pThread`  
 ブレークポイントが発生したスレッドを表す [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) のオブジェクト。  
  
 `bstrContext`  
 コード内のブレークポイントのコンテキスト \(通常は呼び出し履歴に表示されるメソッドまたは関数名。  
  
 `bstrDataExpr`  
 データをユーザーが Enter ブレークポイントを設定するにはにおける文字列。  
  
 `dwNumElements`  
 ブレークポイントが発生したデータの文字列の要素の数。  
  
## 解説  
 この構造体共用体の一部として [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) の構造体のメンバーです。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)