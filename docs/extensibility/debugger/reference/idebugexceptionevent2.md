---
title: "IDebugExceptionEvent2 | Microsoft Docs"
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
  - "IDebugExceptionEvent2"
helpviewer_keywords: 
  - "IDebugExceptionEvent2 インターフェイス"
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExceptionEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

デバッグ エンジンは \(DE\)デバッグ セッションのマネージャー \(SDM\) に例外が現在実行されているプログラムでスローされたときにこのインターフェイスを送信します。  
  
## 構文  
  
```  
IDebugExceptionEvent2 : IUnknown  
```  
  
## 実装についてのメモ  
 DE implements デバッグ対象のプログラムに例外が発生したことを報告します。このインターフェイス  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) のインターフェイスはインターフェイスと同じオブジェクトで実行する必要があります。  SDM は `IDebugEvent2` のインターフェイスへのアクセスに [QueryInterface](/visual-cpp/atl/queryinterface) を使用します。  
  
## 呼び出し元のメモ  
 DE は例外を報告するためこのイベント オブジェクトを作成し送信します。  イベントはSDM によって提供される [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) のコールバック関数を使用してデバッグ対象のプログラムにアタッチしたときに送信されます。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugExceptionEvent2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetException](../Topic/IDebugExceptionEvent2::GetException.md)|このイベントが発生した例外に関する詳細情報を取得します。|  
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|このイベントを発生させたスローされた例外についてユーザーにわかりやすい説明を取得します。|  
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|実行を再開するとデバッグの \(DE\) デバッグ対象のプログラムにこの例外を渡す際のオプション エンジンをサポートするかどうかを指定します。|  
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|実行を再開したときまたは例外が破棄例外をデバッグ中のプログラムに渡す必要があるかどうかを指定します。|  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 解説  
 イベントを送信する前にこの例外が [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) イベントへの前の呼び出しによって初回またはセカンド チャンス例外ので指定されていないかde\-DE を検証します。  初回例外であることを指定する `IDebugExceptionEvent2` のイベントは SDM に送信されます。  そうでない場合はde\-DE はアプリケーションによって例外が処理されます。  例外ハンドラーが指定されていない場合は例外がセカンド チャンス例外として指定すると`IDebugExceptionEvent2` のイベントは SDM に送信されます。  はde\-DE はプログラムの実行を再開してオペレーティング システムまたはランタイムは例外を処理します。  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)