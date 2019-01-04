---
title: IDebugExpressionEvaluationCompleteEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d56671d3e0edecde7d67937e07b70cab335efefe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53963406"
---
# <a name="idebugexpressionevaluationcompleteevent2"></a>IDebugExpressionEvaluationCompleteEvent2
このインターフェイスは、非同期式の評価が完了すると、セッション デバッグ マネージャー (SDM) にデバッグ エンジン (DE) によって送信されます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugExpressionEvaluationCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デへの呼び出しによって開始された式の評価の完了をレポートするには、このインターフェイスを実装する[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)します。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)このインターフェイスと同じオブジェクトでインターフェイスを実装する必要があります。 SDM を使用して[QueryInterface](/cpp/atl/queryinterface)にアクセスする、`IDebugEvent2`インターフェイス。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 デは作成し、式の評価の完了を報告するには、このイベント オブジェクトを送信します。 使用して、イベントが送信される、 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)デバッグ中のプログラムに添付するときに、SDM によって指定されたコールバック関数。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugExpressionEvaluationCompleteEvent2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|元の式を取得します。|  
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|式の評価の結果を取得します。|  
  
## <a name="remarks"></a>Remarks  
 評価の成功または失敗かどうか、デはこのイベントを送信する必要があります。  
  
 評価が、失敗した場合、`DEBUG_PROPINFO_VALUE`と`DEBUG_PROPINFO_ATTRIB`フラグを設定できませんが、 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)によって返される構造[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)オブジェクトは、DE によって作成されで返される、`IDebugExpressionEvaluationCompleteEvent2`イベント評価に失敗した場合)。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)