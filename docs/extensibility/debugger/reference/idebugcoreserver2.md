---
title: "IDebugCoreServer2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer2"
helpviewer_keywords: 
  - "IDebugCoreServer2 インターフェイス"
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugCoreServer2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはネットワークのコンピューターのサーバーからの情報を表し取得するために使用します。  
  
## 構文  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## 実装についてのメモ  
 Visual Studio はサーバーを表すためこのインターフェイスを実装します。  Visual Studio の各インスタンスはこのインターフェイスのインスタンスを作成します。  
  
## 呼び出し元のメモ  
 カスタム ポートのサプライヤー [イベント](../../../extensibility/debugger/reference/idebugportevents2-event.md) はこのインターフェイスの呼び出しを受け取ります。  
  
 デバッグ エンジンは[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) を返すにはこのインターフェイスを [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) \(`IDebugCoreServer2` インターフェイスから派生できます。間接的に派生します。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugCoreServer2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetMachineInfo](../Topic/IDebugCoreServer2::GetMachineInfo.md)|マシンの名前と属性を取得します。|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|コンピューター名を取得します。|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|コンピューターにインストールされているポートの業者を取得します。|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|コンピューターに既に存在するポートを取得します。|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|コンピューターのすべてのポートの列挙子を作成します。|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|マシンのポートのサプライヤーの列挙子を作成します。|  
|[GetMachineUtilities\_V7](../Topic/IDebugCoreServer2::GetMachineUtilities_V7.md)|コンピューターのマシンのユーティリティを取得します。|  
  
## 解説  
 Visual Studio によってこのインターフェイスがネットワークのコンピューターで実行されているプロセスを参照するために使用されます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [イベント](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)