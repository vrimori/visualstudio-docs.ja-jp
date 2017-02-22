---
title: "IDebugSymbolSearchEvent2 | Microsoft Docs"
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
  - "IDebugSymbolSearchEvent2"
helpviewer_keywords: 
  - "IDebugSymbolSearchEvent2"
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolSearchEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはデバッグ エンジン \(DE\) によってデバッグ モジュールのデバッグ シンボルが読み込まれたことを示すために送信されます。  
  
## 構文  
  
```  
IDebugSymbolSearchEvent2 : IUnknown  
```  
  
## 実装についてのメモ  
 DE implements モジュールのシンボルが読み込まれたことを報告します。このインターフェイス  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) のインターフェイスはインターフェイスと同じオブジェクトで実行する必要があります。  SDM は `IDebugEvent2` のインターフェイスへのアクセスに [QueryInterface](/visual-cpp/atl/queryinterface) を使用します。  
  
## 呼び出し元のメモ  
 DE はモジュールのシンボルが読み込まれたことを報告するためこのイベント オブジェクトを作成し送信します。  イベントはSDM によって提供される [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) のコールバック関数を使用してデバッグ対象のプログラムにアタッチしたときに送信されます。  
  
## Vtable の順序でメソッド  
 `IDebugSymbolSearchEvent2` のインターフェイスは次にメソッドを公開します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|シンボル検索の結果についての情報を取得します。|  
  
## 解説  
 このイベントはシンボルが読み込まれていない送信されます。  `IDebugSymbolSearchEvent2::GetSymbolSearchInfo` を呼び出してこのイベントのハンドラーはモジュールが実際にシンボルがあるかどうかを調べることができます。  
  
 Visual Studio には\[出力\] ウィンドウ ENT0ENT のシンボル読み込みの状態を更新するにはこのイベントを使用します。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)