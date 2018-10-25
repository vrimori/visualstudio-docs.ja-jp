---
title: IDebugEngineProgram2 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a28755a87446893d9cff9193d62292af36e2c0ac
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49205193"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このインターフェイスは、マルチ スレッド デバッグのサポートを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugEngineProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジンでは、複数のスレッドの同時デバッグをサポートするには、このインターフェイスを実装します。 このインターフェイスの実装を実装するオブジェクトと同じで、 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)インターフェイス。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 使用[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)からこのインターフェイスを取得する、`IDebugProgram2`インターフェイス。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugEngineProgram2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|このプログラムで実行されているすべてのスレッドを停止します。|  
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|実行 (または実行の監視の停止) を監視する特定のスレッドで発生します。|  
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|プログラムが停止された場合でも、特定のスレッドで発生する式の評価を許可 (または許可されていません)。|  
  
## <a name="remarks"></a>Remarks  
 Visual Studio はこのインターフェイスへの応答を呼び出し、 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)イベントと、プログラムの「ウォッチのスレッドのステップ」と「ウォッチの式の評価でスレッド」の状態を設定します。 [停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)たびに呼び出されますが、プログラムが停止する。 このメソッドは、プログラムのすべてのスレッドを終了する機会を与えます。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

