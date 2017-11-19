---
title: "IDebugApplication110 インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplication110 Interface
ms.assetid: ae943133-eb65-4ddc-a29f-9280a82dd8d6
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd7c283e925db5b42b4d04bfc42ea087ecc22b6f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplication110-interface"></a>IDebugApplication110 インターフェイス
`IDebugApplication110`インターフェイスの機能を拡張する、 [IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)です。 実装での QueryInterface を呼び出すことにより、このインターフェイスのインスタンスを取得することができます[IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)です。  
  
> [!IMPORTANT]
>  このインターフェイスは、PDM v11.0 以降によって実装されます。 activdbg100.h にあります。  
  
## <a name="methods"></a>メソッド  
 `IDebugApplication110` インターフェイスは、以下のメソッドを公開します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugApplication110::SynchronousCallInMainThread](../../winscript/reference/idebugapplication110-synchronouscallinmainthread.md)|メイン スレッドで同期呼び出しを使用します。|  
|[IDebugApplication110::AsynchronousCallInMainThread](../../winscript/reference/idebugapplication110-asynchronouscallinmainthread.md)|メイン スレッドでの非同期呼び出しを使用します。|  
|[IDebugApplication110::CallableWaitForHandles](../../winscript/reference/idebugapplication110-callablewaitforhandles.md)|シグナル状態になる一方で指定したハンドルのいずれかの待機スレッド間の呼び出しに、このスレッドに通知されます。 このメソッドは、デバッガー スレッドから呼び出す必要があります。|