---
title: "IDebugEntryPointEvent2 | Microsoft Docs"
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
  - "IDebugEntryPointEvent2"
helpviewer_keywords: 
  - "IDebugEntryPointEvent2 インターフェイス"
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEntryPointEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

デバッグ エンジンは \(DE\)デバッグ セッションにプログラム マネージャー \(SDM\) がユーザー コードの最初の命令を実行するときにこのインターフェイスを送信します。  
  
## 構文  
  
```  
IDebugEntryPointEvent2 : IUnknown  
```  
  
## 実装についてのメモ  
 DE implements 正常な動作の一部としてこのインターフェイス。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) のインターフェイスはインターフェイスと同じオブジェクトで実行する必要があります。  SDM は `IDebugEvent2` のインターフェイスへのアクセスに [QueryInterface](/visual-cpp/atl/queryinterface) を使用します。  
  
## 呼び出し元のメモ  
 DE でプログラムが読み込まれた後で送信したユーザー コードの最初の命令を実行する準備が整った作成しこのオブジェクトをイベント。  イベントはSDM によって提供される [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) のコールバック関数を使用してデバッグ対象のプログラムにアタッチしたときに送信されます。  
  
## 解説  
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) はプログラムでは一番最初の命令を実行するときに送信されます。  たとえば`IDebugEntryPoint2` はプログラムがユーザーの `main` の関数を実行するときに送信されます。  
  
 DE sends `IDebugEntryPointEvent2` がユーザー コードの最初の命令に現在のコード位置する必要がある場合に `main` のようにします。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)