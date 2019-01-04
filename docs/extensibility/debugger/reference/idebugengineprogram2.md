---
title: IDebugEngineProgram2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 33f1d88eaa7fe6cce34f4b386998ecc68cfe4953
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53934480"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
このインターフェイスは、マルチ スレッド デバッグのサポートを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugEngineProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジンでは、複数のスレッドの同時デバッグをサポートするには、このインターフェイスを実装します。 このインターフェイスの実装を実装するオブジェクトと同じで、 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)インターフェイス。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 使用[QueryInterface](/cpp/atl/queryinterface)からこのインターフェイスを取得する、`IDebugProgram2`インターフェイス。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugEngineProgram2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|このプログラムで実行されているすべてのスレッドを停止します。|  
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|実行 (または実行の監視の停止) を監視する特定のスレッドで発生します。|  
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|プログラムが停止された場合でも、特定のスレッドで発生する式の評価を許可 (または許可されていません)。|  
  
## <a name="remarks"></a>Remarks  
 Visual Studio はこのインターフェイスへの応答を呼び出し、 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)イベントと、プログラムの「ウォッチのスレッドのステップ」と「ウォッチの式の評価でスレッド」の状態を設定します。 [停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)たびに呼び出されますが、プログラムが停止する。 このメソッドは、プログラムのすべてのスレッドを終了する機会を与えます。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)