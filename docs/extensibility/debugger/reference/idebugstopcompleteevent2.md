---
title: "IDebugStopCompleteEvent2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2e92138f969189a33e1a5aad5a083c8ac57852dc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
デバッグ エンジン (DE) は、プログラムが停止したときに、この省略可能なイベントをセッション デバッグ マネージャー (SDM) に送信できます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 これはの新しいインターフェイス[!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]です。 以前のリリースでは、非同期の停止はサポートしませんでした。  
  
 [停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)マルチ プロセスまたは複数のプログラムのシナリオで SDM によって呼び出されます。 1 つのプログラムは、停止イベントを SDM に送信するときに、SDM を停止するには、他のプログラムを要求します。  
  
 プログラムを停止した SDM を非同期に通知するために使用されます。 これはインタープリター デバッグ エンジンでは、場所もコードが実行されていないデバッグ対象のプログラム内、ように[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)同期的に完了することができません。 デバッグ エンジンがこの非同期通知を使用するか、返す必要があります`S_ASYNC_STOP`から[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)です。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll