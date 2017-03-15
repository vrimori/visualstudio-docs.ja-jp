---
title: "IDebugBreakEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakEvent2"
helpviewer_keywords: 
  - "IDebugBreakEvent2 インターフェイス"
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugBreakEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスは非同期中断が正常に完了 \(SDM\) したことを使用したデバッグ セッションのマネージャーに指示します。  
  
## 構文  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## 実装についてのメモ  
 DE implements プログラムのユーザーの中断をサポートするインターフェイス。この  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) のインターフェイスはこのインターフェイス \(`IDebugEvent2` のインターフェイスにアクセス [QueryInterface](/visual-cpp/atl/queryinterface) SDM を使用\) と同じオブジェクトで実行する必要があります。  
  
## 呼び出し元のメモ  
 SDM はユーザーが要求した一時停止にデバッグするプログラムがある場合 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) を呼び出します。  プログラムが正常に一時停止されている場合de\-DE sends `IDebugBreakEvent2` イベント。  このイベントはSDM によって提供される [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) のコールバック関数を使用してデバッグ対象のプログラムにアタッチしたときに送信されます。  
  
## 解説  
 たとえば無限ループを実行しているプログラムが発生する ENT1ENT \[入力\] メニューの  **すべて中断**  のコマンドを選択できます。  SDMプログラムの立寄るように指示し[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) を呼び出します。  プログラムが最終的に停止するときに `IDebugBreakEvent2` sends します。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)