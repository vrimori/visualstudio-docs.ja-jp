---
title: IDebugApplication110 インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110 Interface
ms.assetid: ae943133-eb65-4ddc-a29f-9280a82dd8d6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b13208d6a507ea4ed3157606f358b6b0168180cf
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349557"
---
# <a name="idebugapplication110-interface"></a>IDebugApplication110 インターフェイス
`IDebugApplication110`インターフェイスの機能を拡張する、 [IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)します。 実装の QueryInterface を呼び出すことによってこのインターフェイスのインスタンスを取得できる[IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)します。  
  
> [!IMPORTANT]
>  このインターフェイスは、PDM v11.0 以降によって実装されます。 activdbg100.h にあります。  
  
## <a name="methods"></a>メソッド  
 `IDebugApplication110` インターフェイスは、以下のメソッドを公開します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugApplication110::SynchronousCallInMainThread](../../winscript/reference/idebugapplication110-synchronouscallinmainthread.md)|メイン スレッドで同期呼び出しを実行します。|  
|[IDebugApplication110::AsynchronousCallInMainThread](../../winscript/reference/idebugapplication110-asynchronouscallinmainthread.md)|メイン スレッドで非同期呼び出しを使用します。|  
|[IDebugApplication110::CallableWaitForHandles](../../winscript/reference/idebugapplication110-callablewaitforhandles.md)|シグナル状態になる一方で、指定したハンドルのいずれかの間、待機スレッド間の呼び出しをこのスレッドに投稿します。 このメソッドは、デバッガー スレッドから呼び出す必要があります。|