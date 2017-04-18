---
title: "IDebugExpressionEvaluationCompleteEvent2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 67f767a04b91e4d5fc1139c3dc7eb519f440b2c7
ms.lasthandoff: 04/05/2017

---
# <a name="idebugexpressionevaluationcompleteevent2"></a>IDebugExpressionEvaluationCompleteEvent2
このインターフェイスは、非同期の式の評価が完了すると、セッションのデバッグ マネージャー (SDM) にデバッグ エンジン (DE) によって送信されます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugExpressionEvaluationCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 レポートへの呼び出しによって開始された式の評価が完了するには、このインターフェイスを実装する、DE [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)です。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)このインターフェイスと同じオブジェクトのインターフェイスを実装する必要があります。 SDM を使用して[QueryInterface](/cpp/atl/queryinterface)にアクセスする、`IDebugEvent2`インターフェイスです。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 デを作成し、式の評価の完了を報告するには、このイベント オブジェクトを送信します。 使用して、イベントが送信される、 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)は、デバッグ中のプログラムに添付するときに、SDM によって指定されたコールバック関数。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugExpressionEvaluationCompleteEvent2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|元の式を取得します。|  
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|式の評価の結果を取得します。|  
  
## <a name="remarks"></a>コメント  
 評価が成功したかどうか、デはこのイベントを送信する必要があります。  
  
 評価が、失敗した場合、`DEBUG_PROPINFO_VALUE`と`DEBUG_PROPINFO_ATTRIB`フラグは設定されません、 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)によって返される構造[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)オブジェクトが、DE によって作成されで返される、`IDebugExpressionEvaluationCompleteEvent2`イベント評価に失敗した場合)。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
