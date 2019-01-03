---
title: IDebugStopCompleteEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 39da50c17d4d4b8b02390e0d2960d5696b93b1f2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53932896"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

デバッグ エンジン (DE) は、プログラムが停止した場合は、この省略可能なイベントをセッション デバッグ マネージャー (SDM) に送信できます。

## <a name="syntax"></a>構文

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>実装についてのメモ

このインターフェイスは、Visual Studio 2005 で導入されました。 以前のリリースでは、非同期の停止はサポートされていませんでした。

[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)はマルチ プロセスまたは複数のプログラムのシナリオで SDM によって呼び出されます。 1 つのプログラムは、SDM を停止してからイベントを送信するとき、SDM を停止するには、他のプログラムを要求します。

停止は、プログラムが停止している SDM を非同期的に通知するために使用されます。 通知、SDM のインタープリターのデバッグ エンジンに便利ですが、場合によってコードが実行されているありません、デバッグ対象内プログラム、ため[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)同期的に完了できません。 デバッグ エンジンがこの非同期通知を使用するか、返す必要があります`S_ASYNC_STOP`から[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)します。

## <a name="requirements"></a>必要条件

ヘッダー: msdbg.h

名前空間:Microsoft.VisualStudio.Debugger.Interop

アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll