---
title: "IDebugSourceServerModule | Microsoft Docs"
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
  - "IDebugSourceServerModule インターフェイス"
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSourceServerModule
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

PDB ファイルに含まれるソース サーバーの情報を表します。  
  
## 構文  
  
```  
IDebugSourceServerModule : IUnknown  
```  
  
## 実装についてのメモ  
 このインターフェイスはデバッガーのエンジンによって実装されデバッガーの UI によって実装されます。  
  
## メソッド  
 次の表は `IDebugSourceServerModule` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|ソース サーバーの情報の配列を取得します。|  
  
## 必要条件  
 ヘッダー : Msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll