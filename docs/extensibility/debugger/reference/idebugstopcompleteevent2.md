---
title: "IDebugStopCompleteEvent2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: aa8941decfb4e64906c57b719df711ce8779df9c
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2018
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

デバッグ エンジン (DE) は、プログラムが停止したときに、この省略可能なイベントをセッション デバッグ マネージャー (SDM) に送信できます。

## <a name="syntax"></a>構文

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>実装についてのメモ

このインターフェイスは、Visual Studio 2005 で導入されました。 以前のリリースでは、非同期の停止はサポートしませんでした。

[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)マルチ プロセスまたは複数のプログラムのシナリオで SDM によって呼び出されます。 1 つのプログラムは、停止イベントを SDM に送信するときに、SDM を停止するには、他のプログラムを要求します。

停止については、プログラムが停止した SDM を非同期に通知するために使用されます。 SDM 役に立ちますインタープリター デバッグ エンジンを通知するには、場所もコードが実行されていない、デバッグ対象内のプログラム、そのため[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)同期的に完了することができません。 デバッグ エンジンがこの非同期通知を使用するか、返す必要があります`S_ASYNC_STOP`から[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)です。

## <a name="requirements"></a>必要条件

ヘッダー: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll