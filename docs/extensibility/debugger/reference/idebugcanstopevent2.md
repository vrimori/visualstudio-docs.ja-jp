---
title: "IDebugCanStopEvent2 | Microsoft Docs"
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
  - "IDebugCanStopEvent2"
helpviewer_keywords: 
  - "IDebugBreakpointRequest2 インターフェイス"
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCanStopEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

現在のコード位置で停止するにはこのインターフェイスが \(SDM\) デバッグ セッションの部下であるかどうかを確認するために使用されます。  
  
## 構文  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジンは \(DE\)ソース・コードのステップ実行をサポートするにはこのインターフェイスを実装します。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) のインターフェイスはこのインターフェイス \(`IDebugEvent2` のインターフェイスにアクセス [QueryInterface](/visual-cpp/atl/queryinterface) SDM を使用\) と同じオブジェクトで実行する必要があります。  
  
 このインターフェイスの実装はデバッグ エンジンに SDM の [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) の呼び出しを伝える必要があります。  たとえばデバッグ エンジンのメッセージ処理のスレッドにポストされるというメッセージができます。またこのインターフェイスを実装するオブジェクトは `IDebugCanStopEvent2::CanStop` に渡されたフラグを持つデバッグ エンジンに再度デバッグ エンジンからへの参照を保持できます。  
  
## 呼び出し元のメモ  
 DE は実行を続けるようにしますがで機能しますがコードをステップ実行するたびにこのメソッドを送信できます。  このイベントはSDM によって提供される [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) のコールバック関数を使用してデバッグ対象のプログラムにアタッチしたときに送信されます。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugCanStopEvent2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetReason](../Topic/IDebugCanStopEvent2::GetReason.md)|このイベントの理由を取得します。|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|デバッグ対象がこのイベントの場所 \(停止の理由を説明する送信するイベント\) を停止し実行を継続するかどうかを指定します。|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|このイベントの場所を示すドキュメントのコンテキストを取得します。|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|このイベントの場所を示すコード コンテキストを取得します。|  
  
## 解説  
 ソース・コードがその場所で表示するかどうかが関数の検索と de\-DE にデバッグ情報またはデバッグ情報が存在していても実際には行わない限りde\-DE sends このインターフェイスは認識します。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)