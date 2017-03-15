---
title: "IDebugPortSupplierEx2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugPortSupplierEx2 インターフェイス"
ms.assetid: dae0050a-a50a-4f35-bfbd-e538f537b20f
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugPortSupplierEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ポートがサプライヤーのコア サーバーによって選択しデータと対話するためのサポートを提供します。  
  
## 構文  
  
```  
IDebugPortSupplierEx2 : IUnknown  
```  
  
## 実装についてのメモ  
 カスタム ポートの業者を使用するコア サーバーを選択できるようにこのインターフェイスを実装します。  
  
## メソッド  
 次の表は **IDebugPortSupplierEx2** のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[SetServer](../../../extensibility/debugger/reference/idebugportsupplierex2-setserver.md)|ポートのサプライヤーのコア サーバーを設定します。|  
  
## 必要条件  
 ヘッダー : Portpriv.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)