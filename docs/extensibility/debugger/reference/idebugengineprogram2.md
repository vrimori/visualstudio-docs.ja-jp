---
title: "IDebugEngineProgram2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngineProgram2
helpviewer_keywords: IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 896370d83634580e46f666a8fb9f56f768bf06a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
このインターフェイスは、マルチ スレッドのデバッグのサポートを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugEngineProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジンでは、複数のスレッドを同時にデバッグをサポートするためにこのインターフェイスを実装します。 このインターフェイスは、同じオブジェクトを実装するには[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)インターフェイスです。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 使用して[QueryInterface](/cpp/atl/queryinterface)からこのインターフェイスを取得、`IDebugProgram2`インターフェイスです。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugEngineProgram2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|このプログラムで実行されているすべてのスレッドを停止します。|  
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|実行 (または実行の監視を停止) を監視する特定のスレッドで発生します。|  
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|プログラムが停止された場合でも、特定のスレッドで発生する式の評価を許可 (または許可されていません) します。|  
  
## <a name="remarks"></a>コメント  
 Visual Studio はこのインターフェイスへの応答を呼び出して、 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)イベントとプログラムの「ウォッチのスレッド ステップ」と「ウォッチの式評価でスレッド」の状態を設定します。 [停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)するたびに呼び出されますが、プログラムが停止する。 このメソッドにより、プログラムをすべてのスレッドを終了する可能性です。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)