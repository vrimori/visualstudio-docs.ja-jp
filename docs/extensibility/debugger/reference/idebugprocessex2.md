---
title: "IDebugProcessEx2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcessEx2"
helpviewer_keywords: 
  - "IDebugProcessEx2 インターフェイス"
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# IDebugProcessEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはにアタッチするか\(SDM\) プロセスからデタッチするにはデバッグ セッションのプロセスがマネージャーに通知することができます。  
  
## 構文  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## 実装についてのメモ  
 カスタム ポートの業者は [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) インターフェイスと同じオブジェクトがこのインターフェイスを実装しています :  
  
-   プロセスに接続されるセッション状態管理をサポートします。  
  
-   複数のデバッグ エンジンでサポートの自動アタッチ  
  
 カスタム ポートのサプライヤーを選択するとこのインターフェイスを実装できます。  
  
## 呼び出し元のメモ  
  
-   SDM はこのインターフェイスを取得するに `IDebugProcess2` のインターフェイス [QueryInterface](/visual-cpp/atl/queryinterface) を呼び出します。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugProcessEx2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|セッションはプロセスをデバッグするプロセスを通知します。|  
|[Detach](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|セッションが既にプロセスをデバッグするプロセスを通知します。|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|デバッグ エンジンの一覧のプログラム ノードを追加します。|  
  
## 解説  
 このインターフェイスはSDM とプロセス間でプライベートです。  
  
## 必要条件  
 ヘッダー : Portpriv.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)