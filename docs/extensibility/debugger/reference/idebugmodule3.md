---
title: "IDebugModule3 | Microsoft Docs"
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
  - "IDebugModule3"
helpviewer_keywords: 
  - "IDebugModule3 インターフェイス"
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugModule3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはシンボルの JustMyCode 状態の別の場所をサポートするモジュールを表します。  
  
## 構文  
  
```  
IDebugModule3 : IDebugModule2  
```  
  
## 実装についてのメモ  
 デバッグ エンジンはシンボル \(DE\) の別の場所をサポートしの JustMyCode 状態を使用するにはこのインターフェイスを実装します \(「 JustMyCode 」の定義については [Visual Studio デバッガーの用語集](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) を参照してください。  
  
## 呼び出し元のメモ  
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) の呼び出しはこのインターフェイスを返します。  DE sends [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) メソッドを使用してデバッグ セッションの [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) マネージャー \(SDM\) へのインターフェイス。  また[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) のインターフェイス [QueryInterface](/visual-cpp/atl/queryinterface) の呼び出しはこのインターフェイスを返します。  
  
## Vtable の順序でメソッド  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) のインターフェイスのメソッド以外にもこのインターフェイスには次のメソッドを実行します :  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|各パスを検索するシンボルを検索するパスと結果のリストを返します。|  
|[LoadSymbols](../Topic/IDebugModule3::LoadSymbols.md)|現在のモジュールの読み込みと初期化のシンボル。|  
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|はモジュールがユーザー コードを表すかどうかの指定を検出します。|  
|[SetJustMyCodeState](../Topic/IDebugModule3::SetJustMyCodeState.md)|モジュールがユーザー コードとして考慮する必要があるかどうかを指定します。|  
  
## 解説  
 Visual Studio はこのインターフェイスの一般的なコンシューマーです。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)