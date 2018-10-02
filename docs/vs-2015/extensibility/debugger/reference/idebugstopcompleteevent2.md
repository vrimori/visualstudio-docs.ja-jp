---
title: IDebugStopCompleteEvent2 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f880888ab675fc7923b50e3b1fbce144f8108abd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546483"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugStopCompleteEvent2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugstopcompleteevent2)します。  
  
デバッグ エンジン (DE) は、プログラムが停止した場合は、この省略可能なイベントをセッション デバッグ マネージャー (SDM) に送信できます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 これは、新しいインターフェイス[!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]します。 以前のリリースでは、非同期の停止はサポートされていませんでした。  
  
 [停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)はマルチ プロセスまたは複数のプログラムのシナリオで SDM によって呼び出されます。 1 つのプログラムは、SDM を停止してからイベントを送信するとき、SDM を停止するには、他のプログラムを要求します。  
  
 SDM プログラムが停止したことを非同期に通知するために使用されます。 場合によってコードが実行されているないデバッグ対象のプログラム内で、これは、インタープリターのデバッグ エンジンに役立ちますように[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)同期的に完了できません。 デバッグ エンジンがこの非同期通知を使用するか、返す必要があります`S_ASYNC_STOP`から[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll

