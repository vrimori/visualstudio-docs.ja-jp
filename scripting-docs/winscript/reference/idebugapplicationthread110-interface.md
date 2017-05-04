---
title: "IDebugApplicationThread110 インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread110 インターフェイス"
ms.assetid: 25bc351f-3451-4387-9302-078f6292ddff
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplicationThread110 インターフェイス
[IDebugApplicationThread インターフェイス](../../winscript/reference/idebugapplicationthread-interface.md) のインターフェイスに機能を提供します。  
  
> [!IMPORTANT]
>  このインターフェイスは PDM v11.0 を超えるによって実装されます。  activdbg100.h.である。  
  
## メソッド  
 `IDebugApplicationThread110` インターフェイスは、以下のメソッドを公開します。  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugApplicationThread110::AsynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread110-asynchronouscallintothread.md)|メイン スレッドで非同期呼び出しを行います。|  
|[IDebugApplicationThread110::GetActiveThreadRequestCount](../../winscript/reference/idebugapplicationthread110-getactivethreadrequestcount.md)|PDM のスレッドの切り替え機構からの要求数のスレッドが現在処理中かの数。  1 種類のスレッドの呼び出しが処理を開始し、トリガー、スレッドの同期するために明示または、スレッドを中断します。通常は 0 か 1 つがしますが、これは最に対して実行する \(たとえば、デバッガーのスレッドで問題 IDebugApplicationEvents のトリガーによってイベント\)|  
|[IDebugApplicationThread110::IsSuspendedForBreakPoint](../../winscript/reference/idebugapplicationthread110-issuspendedforbreakpoint.md)|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) はこのスレッドで、まだ完了しましたがありません。|  
|[IDebugApplicationThread110::IsThreadCallable](../../winscript/reference/idebugapplicationthread110-isthreadcallable.md)|このスレッドは PDM のスレッドの切り替え機構を使用しての呼び出しを処理できる状態になります \(SynchronousCallInThread など\)。|