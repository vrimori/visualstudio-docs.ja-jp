---
title: "IDebugPortSupplier3 | Microsoft Docs"
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
  - "IDebugPortSupplier3"
helpviewer_keywords: 
  - "IDebugPortSupplier3 インターフェイス"
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortSupplier3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスは呼び出し元がサプライヤーのポートをデバッガー呼び出しのポート \(ディスクにして記述して\) は保持しそのリストに保持されたポートを取得できるかどうかを判断します。  
  
## 構文  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## 実装についてのメモ  
 カスタム ポートの業者はディスクに永続化または保存するポート情報をサポートするにはこのインターフェイスを実装します。  このインターフェイスは [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) のインターフェイスと同じオブジェクトで実行する必要があります。  
  
## 呼び出し元のメモ  
 このインターフェイスを取得 `IDebugPortSupplier2` のインターフェイスでは [QueryInterface](/visual-cpp/atl/queryinterface)。  
  
## Vtable の順序でメソッド  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) のインターフェイスから継承されるメソッドに加えてこのインターフェイスは以下をサポートします :  
  
|メソッド|Description|  
|----------|-----------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|ポートのサプライヤーがデバッガーの呼び出し \(ディスクにして記述して\) を保持するのかを返します。|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|このポートの仕入先にディスクに作成されたすべてのポートを列挙するために使用できるオブジェクトを返します。|  
  
## 解説  
 ポートがサプライヤーの呼び出しにおける保持できるポートこのインターフェイスを実装します。  ポートはポートのサプライヤーが破棄されるときにそのポートのサプライヤーがディスクにインスタンス化され作成されたときに読み込まれる必要があります。  
  
 デバッグ エンジンは通常サプライヤーのポートとやり取りしてこのインターフェイスに表示方向がありません。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)