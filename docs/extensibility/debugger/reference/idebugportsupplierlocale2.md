---
title: "IDebugPortSupplierLocale2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugPortSupplierLocale2 インターフェイス"
ms.assetid: 910e7220-da2a-4339-9fff-9fb1bad3c28c
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortSupplierLocale2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ポートの仕入先にロケールをサポートします。  
  
## 構文  
  
```  
IDebugPortSupplierLocale2 : IUnknown  
```  
  
## 実装についてのメモ  
 カスタム ポートの業者はロケールを設定するにはこのインターフェイスを実装します。  
  
## メソッド  
 次の表は **IDebugPortSupplierLocale2** のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[Setlocale 関数](../../../extensibility/debugger/reference/idebugportsupplierlocale2-setlocale.md)|ポートのサプライヤーのロケールを設定します。|  
  
## 必要条件  
 ヘッダー : Portpriv.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)