---
title: "IDebugApplicationThreadEvents110 インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThreadEvents110 インターフェイス"
ms.assetid: 91a98b0e-7c81-4118-af75-82f75fd4f25a
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplicationThreadEvents110 インターフェイス
より多くのスレッドのイベントを追加します。  これらのイベントは、ローカルです。  つまり、アドバイス [IConnectionPoint](http://go.microsoft.com/fwlink/?LinkId=232738) を使用して、デバッグ対象のプロセスのみにサブスクライブし、PDM アプリケーションの unadvise のメソッドはオブジェクト \( [IDebugApplicationThread インターフェイス](../../winscript/reference/idebugapplicationthread-interface.md)を実装するオブジェクト\) に保持します。  これらはから移行したスレッドで発生します。  
  
> [!IMPORTANT]
>  このインターフェイスは PDM v11.0 を超えるによって実装されます。  activdbg100.h.である。  
  
## メソッド  
 `IDebugActivationThreadEvents110` インターフェイスは、以下のメソッドを公開します。  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|PDM のスレッドの切り替えを使用してスレッドの呼び出しが開始されました。|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|スレッドは、ブレークポイントから再開して、再度アクティブになります。|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|スレッドは、ブレークポイントで中断して、スレッドが完全に中断する必要のある呼び出しを処理できます。|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|PDM のスレッドの切り替えを使用してスレッドの呼び出しが完了する|