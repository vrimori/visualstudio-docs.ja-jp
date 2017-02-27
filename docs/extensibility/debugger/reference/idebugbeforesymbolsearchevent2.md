---
title: "IDebugBeforeSymbolSearchEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugBeforeSymbolSearchEvent2 インターフェイス"
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugBeforeSymbolSearchEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

デバッグ エンジンはセッション \(DE\) マネージャー \(SDM\) にデバッグ シンボルの読み込み中にステータス バーのメッセージを設定するにはこのインターフェイスを送信します。  
  
## 構文  
  
```  
IDebugBeforeSymbolSearchEvent2 : IUnknown  
```  
  
## 実装についてのメモ  
 シンボルの実行中にステータス バーのメッセージを設定するときにこのインターフェイスを読み込む implements します。  このインターフェイスが実装され動作またはスクリプトのインタープリターの一部にデバッグ エンジンになります。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) のインターフェイスはこのインターフェイス \(インターフェイスにアクセス **IDebugEvent2** SDM の **QueryInterface** 使用\) と同じオブジェクトで実行する必要があります。  
  
## 呼び出し元のメモ  
 DE はシンボルの読み込み中にステータス バーのメッセージを設定する必要がある場合はこのイベント オブジェクトを作成し送信します。  イベントはSDM によって提供される [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) のコールバック関数を使用してデバッグ対象のプログラムにアタッチしたときに送信されます。  
  
## メソッド  
 次の表は `IDebugBeforeSymbolSearchEvent2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|現在デバッグ モジュールの名前を取得します。|  
  
## 必要条件  
 ヘッダー : Msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll