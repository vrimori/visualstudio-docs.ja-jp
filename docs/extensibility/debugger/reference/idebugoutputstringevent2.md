---
title: "IDebugOutputStringEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugOutputStringEvent2"
helpviewer_keywords: 
  - "IDebugOutputStringEvent2 インターフェイス"
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugOutputStringEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはデバッグ セッションのマネージャー \(SDM\) にデバッグ エンジン \(DE\) で文字列を出力するに送信されます。  
  
## 構文  
  
```  
IDebugOutputStringEvent2 : IUnknown  
```  
  
## 実装についてのメモ  
 DE implements IDE の ENT0ENT \[出力\] ウィンドウに文字列を送信する。このインターフェイス  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) のインターフェイスはインターフェイスと同じオブジェクトで実行する必要があります。  SDM は `IDebugEvent2` のインターフェイスへのアクセスに [QueryInterface](/visual-cpp/atl/queryinterface) を使用します。  
  
## 呼び出し元のメモ  
 DE ENT0ENT は\[出力\] ウィンドウに文字列を送信するにはこのイベント オブジェクトを作成し送信します。  イベントはSDM によって提供される [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) のコールバック関数を使用してデバッグ対象のプログラムにアタッチされたときに送信されます。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugOutputStringEvent2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetString](../Topic/IDebugOutputStringEvent2::GetString.md)|表示するメッセージを取得します。|  
  
## 解説  
 たとえばアンマネージ コードに出力された文字列はWin32 の関数に送信 `OutputDebugString` デバッグするプログラム文字列を作成できます。  この文字列は de\-DE によって傍受されSDM に `IDebugOutputStringEvent2` のイベントとして送信されます。  
  
 ユーザーの応答が必要なメッセージを送信するために [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) を使用します。  
  
 応答を必要としないエラー メッセージを送信するために [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) を使用します。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)