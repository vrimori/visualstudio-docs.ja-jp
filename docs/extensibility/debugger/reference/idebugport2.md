---
title: "IDebugPort2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPort2"
helpviewer_keywords: 
  - "IDebugPort2 インターフェイス"
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugPort2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはコンピューターのデバッグ ポートを表します。  
  
## 構文  
  
```  
IDebugPort2 : IUnknown  
```  
  
## 実装についてのメモ  
 カスタム ポートのサプライヤーがコンピューターのデバッグ ポートを表すためこのインターフェイスを実装します。  
  
 ポートがポート イベントの送信をサポートする場合[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)インターフェイスを使用して <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> のインターフェイスをサポートするに <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> のインターフェイスを実装する必要があります。  
  
## 呼び出し元のメモ  
 [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) または [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) の呼び出し要求されたポートを表すインターフェイス。この  
  
## Vtable の順序でメソッド  
 次の表は `IDebugPort2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|ポート名を返します。|  
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|ポートの識別子を返します。|  
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|ポートの作成に使用される要求を返します \(存在する場合\)。|  
|[GetPortSupplier](../Topic/IDebugPort2::GetPortSupplier.md)|このポートのポートの業者を返します。|  
|[GetProcess](../Topic/IDebugPort2::GetProcess.md)|プロセス ID を持つプロセスへのインターフェイスを返します。|  
|[EnumProcesses](../Topic/IDebugPort2::EnumProcesses.md)|ポートで実行されているプロセスを列挙します。|  
  
## 解説  
 ローカル ポートがローカル コンピューターで実行されているすべてのプロセスとプログラムへのアクセスを提供します。  他のポートはWindows CE ベースのデバイスに不良シリアル接続非 DCOM コンピューターにネットワーク接続を表す場合があります。  `IDebugPort2` のインターフェイスがポートの名前と ID を検索しポートで実行されているプロセスを列挙しポートでプロセスを開始および終了する機能を提供するために使用されます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)