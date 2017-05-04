---
title: "IDebugApplication110 インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplication110 インターフェイス"
ms.assetid: ae943133-eb65-4ddc-a29f-9280a82dd8d6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplication110 インターフェイス
`IDebugApplication110` のインターフェイスは [IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)の機能を拡張します。  [IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)の実装の QueryInterface を呼び出して、このインターフェイスのインスタンスを取得できます。  
  
> [!IMPORTANT]
>  このインターフェイスは PDM v11.0 を超えるによって実装されます。  activdbg100.h.である。  
  
## メソッド  
 `IDebugApplication110` インターフェイスは、以下のメソッドを公開します。  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugApplication110::SynchronousCallInMainThread](../../winscript/reference/idebugapplication110-synchronouscallinmainthread.md)|メイン スレッドで同期呼び出しを行います。|  
|[IDebugApplication110::AsynchronousCallInMainThread](../../winscript/reference/idebugapplication110-asynchronouscallinmainthread.md)|メイン スレッドで非同期呼び出しを行います。|  
|[IDebugApplication110::CallableWaitForHandles](../../winscript/reference/idebugapplication110-callablewaitforhandles.md)|このスレッドにポストされるように、スレッド間呼び出しの中に通知を送信する指定したハンドルのいずれかの待機時間。  このメソッドは、デバッガーのスレッドから呼び出す必要があります。|