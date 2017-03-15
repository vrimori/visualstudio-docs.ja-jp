---
title: "IDebugDefaultPort2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDefaultPort2"
helpviewer_keywords: 
  - "IDebugDefaultPort2 インターフェイス"
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDefaultPort2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはポートのサーバーと通知機能にアクセスするためのメソッドを提供します。  
  
## 構文  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## 実装についてのメモ  
 Visual Studio はプログラムにアクセスするためのデバッグ ポートを表すためこのインターフェイスを実装します。  カスタム ポートの業者はリモート デバッグを処理する場合このインターフェイスを実装できます。  
  
## 呼び出し元のメモ  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) インターフェイスのメソッドへの引数はこのインターフェイスを提供します。  [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) のインターフェイス [QueryInterface](/visual-cpp/atl/queryinterface) を呼び出してこのインターフェイスを取得できます。  
  
## Vtable の順序でメソッド  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) で定義したメソッドに加えてこのインターフェイスは以下のメソッドを実行します :  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetPortNotify](../Topic/IDebugDefaultPort2::GetPortNotify.md)|このポートからの通知インターフェイスを取得します。|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|ホスト サーバーにインターフェイスこのポートを取得します。|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|このポートがローカル コンピューターで実行されているかどうかを判定します。|  
  
## 解説  
 既定のポートがないため名前は」 「 `IDebugDefaultPort2`正しい名称ビットです。  「」と IDebugPort3 呼び出すことができます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)