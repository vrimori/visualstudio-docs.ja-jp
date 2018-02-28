---
title: "IDebugApplicationThread110 インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110 Interface
ms.assetid: 25bc351f-3451-4387-9302-078f6292ddff
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aee30ae68319810f58bf31f8d0eb32cf8f30d34c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthread110-interface"></a>IDebugApplicationThread110 インターフェイス
複数の機能を提供、 [IDebugApplicationThread インターフェイス](../../winscript/reference/idebugapplicationthread-interface.md)インターフェイスです。  
  
> [!IMPORTANT]
>  このインターフェイスは、PDM v11.0 以降によって実装されます。 activdbg100.h にあります。  
  
## <a name="methods"></a>メソッド  
 `IDebugApplicationThread110` インターフェイスは、以下のメソッドを公開します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugApplicationThread110::AsynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread110-asynchronouscallintothread.md)|メイン スレッドでの非同期呼び出しを使用します。|  
|[IDebugApplicationThread110::GetActiveThreadRequestCount](../../winscript/reference/idebugapplicationthread110-getactivethreadrequestcount.md)|メカニズムを切り替え PDM のスレッドからスレッド要求の数が現在処理中の数。 0 または 1 ですが、それが高い場合 1 つのスレッド呼び出し処理が開始スレッドからの同期呼び出しをトリガーやそれ以外の場合 (たとえば、デバッガーで発行される IDebugApplicationEvents イベントをトリガーすることによって、スレッドを中断する可能性の通常スレッド)|  
|[IDebugApplicationThread110::IsSuspendedForBreakPoint](../../winscript/reference/idebugapplicationthread110-issuspendedforbreakpoint.md)|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)がこのスレッドで呼び出されており、まだ完了していません。|  
|[IDebugApplicationThread110::IsThreadCallable](../../winscript/reference/idebugapplicationthread110-isthreadcallable.md)|このスレッドは、PDM のスレッドの機構 (SynchronousCallInThread) などの切り替えを使用して行われた呼び出しを処理できる状態です。|