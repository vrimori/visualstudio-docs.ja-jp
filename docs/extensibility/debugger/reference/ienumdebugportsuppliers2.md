---
title: "IEnumDebugPortSuppliers2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPortSuppliers2"
helpviewer_keywords: 
  - "IEnumDebugPortSuppliers2"
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IEnumDebugPortSuppliers2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはポートの業者を列挙します。  
  
## 構文  
  
```  
IEnumDebugPortSuppliers2 : IUnknown  
```  
  
## 実装についてのメモ  
 Visual Studio はポートの業者の一覧を表すにはこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 ポートの業者の一覧を取得するに [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) を呼び出します。  
  
## Vtable の順序でメソッド  
 次の表は `IEnumDebugPortSuppliers2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[次へ](../Topic/IEnumDebugPortSuppliers2::Next.md)|列挙体シーケンスのポートのサプライヤーの指定した数を取得します。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|列挙体シーケンスのポートのサプライヤーの指定した数の要素をスキップします。|  
|[リセット](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|列挙体シーケンスを先頭にリセットします。|  
|[複製](../Topic/IEnumDebugPortSuppliers2::Clone.md)|現在の列挙子と同じ列挙状態を含む列挙子を作成します。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|列挙子のポートのサプライヤーの数を取得します。|  
  
## 解説  
 デバッグ エンジンは通常はこのインターフェイスを取得する必要はありません。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)