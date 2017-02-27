---
title: "IDebugDynamicFieldCOMPlus | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugDynamicFieldCOMPlus インターフェイス"
ms.assetid: c3a25f27-327a-4bdb-b026-27d436ddcd0c
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugDynamicFieldCOMPlus
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) のオブジェクトの動的フィールドを表します。  
  
## 構文  
  
```  
IDebugDynamicFieldCOMPlus : IDebugDynamicField  
```  
  
## メソッド  
 [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md) のインターフェイスのメソッド以外にもこのインターフェイスには次のメソッドを実行します :  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetTypeFromPrimitive](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromprimitive.md)|プリミティブ型の型を取得します。|  
|[GetTypeFromTypeDef](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromtypedef.md)|トークンの型を取得します。|  
  
## 必要条件  
 ヘッダー : Sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll