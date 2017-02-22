---
title: "IDebugDynamicField | Microsoft Docs"
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
  - "IDebugDynamicField"
helpviewer_keywords: 
  - "IDebugDynamicField インターフェイス"
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDynamicField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスは変数の型を表します。  
  
## 構文  
  
```  
IDebugDynamicField : IDebugField  
```  
  
## 実装についてのメモ  
 このインターフェイスは実行時に決定する必要がある型の基本クラスとしてシンボルのプロバイダーによって実装されます。  これはマネージ コード専用です。  
  
## 呼び出し元のメモ  
 このインターフェイスはインターフェイスを取得できます。特化した基本クラスを表します。  
  
## Vtable の順序でメソッド  
 このインターフェイスは `IDebugField` から継承されていないメソッドは用意されていません。  
  
## 必要条件  
 ヘッダー : sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [シンボルのプロバイダー インターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)