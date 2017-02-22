---
title: "IDebugProcessQueryProperties | Microsoft Docs"
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
  - "IDebugProcessQueryProperties"
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcessQueryProperties
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスは [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) の実装によって実装される機能拡張インターフェイスです。  モデルは実装がデバッグ プロセスの環境情報を取得するようにします。  
  
## 構文  
  
```  
IDebugProcessQueryProperties: IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ プロセスの実行環境情報を取得するにはこのインターフェイスを実装します。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugProcessQueryProperties` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[QueryProperty](../Topic/IDebugProcessQueryProperties::QueryProperty.md)|プロパティ値を照会します。|  
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|プロパティ値を照会します。|  
  
## 解説  
 このインターフェイスは実装されていません。  
  
## 必要条件  
 ヘッダー : Portpriv.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)