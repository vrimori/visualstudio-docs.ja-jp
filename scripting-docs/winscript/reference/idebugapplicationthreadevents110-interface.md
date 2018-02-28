---
title: "IDebugApplicationThreadEvents110 インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110 Interface
ms.assetid: 91a98b0e-7c81-4118-af75-82f75fd4f25a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6aaf312b1730696b812172aeea175619e911d03a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthreadevents110-interface"></a>IDebugApplicationThreadEvents110 インターフェイス
複数のスレッド イベントを追加します。 これらのイベントはローカルのみです。 サブスクライブできますに対象のプロセスでのみを使用して、デバッグ、 [IConnectionPoint](http://go.microsoft.com/fwlink/?LinkId=232738)アドバイスし、PDM アプリケーション スレッド オブジェクトでメソッドをアドバイズ (を実装するオブジェクト[IDebugApplicationThreadインターフェイス](../../winscript/reference/idebugapplicationthread-interface.md))。 送信されているスレッドで発生するとします。  
  
> [!IMPORTANT]
>  このインターフェイスは、PDM v11.0 以降によって実装されます。 activdbg100.h にあります。  
  
## <a name="methods"></a>メソッド  
 `IDebugActivationThreadEvents110` インターフェイスは、以下のメソッドを公開します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|呼び出しスレッドは、PDM のスレッドを使用して、切り替えが開始されました。|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|スレッドは、ブレークポイントから再開して、もう一度有効になります。|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|スレッドでは、ブレークポイントの中断とが完全に中断されるスレッドを必要とする呼び出しを処理できます。|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|呼び出しスレッドは、PDM のスレッドを使用して、切り替えが完了しました。|