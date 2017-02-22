---
title: "IDebugCoreServer3 | Microsoft Docs"
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
  - "IDebugCoreServer3"
helpviewer_keywords: 
  - "IDebugCoreServer3 インターフェイス"
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCoreServer3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはプロセスが実行されているサーバーに関する情報にアクセスできます。  
  
## 構文  
  
```  
IDebugCoreServer3 : IDebugCoreServer2  
```  
  
## 実装についてのメモ  
 Visual Studio はこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) のインターフェイスからこのインターフェイスを取得するに [QueryInterface](/visual-cpp/atl/queryinterface) を使用します。  [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) の呼び出しはこのインターフェイスを返すことができます。  カスタム ポートの仕入先には最も一般にこのインターフェイスはサーバーのプログラムの起動に使用されます \(ローカルまたはリモート\)。  
  
## Vtable の順序でメソッド  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) のインターフェイスのメソッド以外にもこのインターフェイスには次のメソッドを実行します :  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|サーバーの名前を取得します。|  
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|サーバー名のわかりやすいバージョンを取得します|  
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|特定のデバッグ エンジンはこれらのプロセスの起動時に自動的にプロセスにアタッチするように指定します。|  
|[DiagnoseWebDebuggingError](../Topic/IDebugCoreServer3::DiagnoseWebDebuggingError.md)|自動アタッチに失敗したときに特定のエラー コードを取得します。|  
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|サーバーのデバッグ エンジンのインスタンスを作成します。|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|呼び出し元がサーバーと同じコンピューターにあるかどうかを示すフラグを取得します。|  
|[GetConnectionProtocol](../Topic/IDebugCoreServer3::GetConnectionProtocol.md)|サーバーとの通信に使用されるプロトコルを示す値を取得します。|  
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|このサーバーがわかっているすべてのデバッグ エンジンのすべての自動アタッチが行われなくなります。|  
  
## 解説  
 カスタム ポートの業者は [イベント](../../../extensibility/debugger/reference/idebugportevents2-event.md) の呼び出しの [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) のインターフェイスを受け取ります。  `IDebugCoreServer3` のインターフェイスはインターフェイスから取得できます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)