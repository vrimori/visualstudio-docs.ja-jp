---
title: "IDebugProgramCreateEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramCreateEvent2"
helpviewer_keywords: 
  - "IDebugProgramCreateEvent2 インターフェイス"
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProgramCreateEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはデバッグ セッションのマネージャー \(SDM\) にデバッグ エンジン \(DE\) によってプログラムがアタッチされたときに送信されます。  
  
## 構文  
  
```  
IDebugProgramCreateEvent2 : IUnknown  
```  
  
## 実装についてのメモ  
 プログラムがアタッチされるとします。カスタム ポートの業者はプログラムが作成されたことを報告します。通常このインターフェイスを実装します。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) のインターフェイスはインターフェイスと同じオブジェクトで実行する必要があります。  SDM は `IDebugEvent2` のインターフェイスへのアクセスに `QueryInterface` のメソッドを使用します。  
  
## 呼び出し元のメモ  
 DE またはカスタム ポートの業者はプログラムの作成を報告するためこのイベント オブジェクトを作成し送信します。  DE sends デバッグ対象のプログラムにアタッチするときの SDM によって提供される [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) のコールバック関数を使用してこのイベント。  カスタム ポートの業者は [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) のインターフェイスを使用してこのイベントを送信します。  
  
## 解説  
 DE またはカスタム ポートの業者は [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md) を呼び出して [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) に新しいインターフェイスを公開します。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)