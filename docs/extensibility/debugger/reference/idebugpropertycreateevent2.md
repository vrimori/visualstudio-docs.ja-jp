---
title: "IDebugPropertyCreateEvent2 | Microsoft Docs"
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
  - "IDebugPropertyCreateEvent2"
helpviewer_keywords: 
  - "IDebugPropertyCreateEvent2 インターフェイス"
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPropertyCreateEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはデバッグ セッションのマネージャー \(SDM\) にデバッグ エンジン \(DE\) によって特定のドキュメントに関連付けられたプロパティを作成するときに送信されます。  
  
## 構文  
  
```  
IDebugPropertyCreateEvent2 : IUnknown  
```  
  
## 実装についてのメモ  
 DE implements プロパティが作成されたことを報告します。このインターフェイス  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) のインターフェイスはインターフェイスと同じオブジェクトで実行する必要があります。  SDM は `IDebugEvent2` のインターフェイスへのアクセスに [QueryInterface](/visual-cpp/atl/queryinterface) を使用します。  このインターフェイスは機能しますがそのスクリプトが IDE に表示される必要がある場合は読み込まれたか作成したスクリプトに関連付けられたプロパティを作成して実行されます。  
  
## 呼び出し元のメモ  
 DE を作成し送信このプロパティを報告するイベント オブジェクトを作成しています。  イベントはSDM によって提供される [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) のコールバック関数を使用してデバッグ対象のプログラムにアタッチされたときに送信されます。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugPropertyCreateEvent2` のインターフェイスのメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|新しいプロパティを取得します。|  
  
## 解説  
 プロパティに関連付けられた特定の文書またはスクリプトがある場合はde\-DE SDM にドキュメントの名前で ENT0ENT \[出力\] ウィンドウを更新するにはこのイベントを送信できます。  [IUnknown](/visual-cpp/atl/iunknown) のポインターを含む `VARIANT` を取得する引数 `guidDocument` SDM では[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)。  \[ENT0ENT\] ウィンドウを更新するために使用される [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) のインターフェイスを取得します。このポインターの [QueryInterface](/visual-cpp/atl/queryinterface) SDM を呼び出します。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)