---
title: IDebugExpression2 |Microsoft Docs
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
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3db1107ced3601f32ea06857386220b282e6af3c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49217058"
---
# <a name="idebugexpression2"></a>IDebugExpression2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このインターフェイスは、バインディング、および評価するための準備ができて解析された式を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) は、すぐに評価できる解析の式を表すためには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出し[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)このインターフェイスを返します。 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)を返します、 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)インターフェイス。 これらのインターフェイスは、デバッグ中のプログラムが一時停止されているし、スタック フレームは、使用可能な場合にのみアクセスできます。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugExpression2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|この式を非同期に評価します。|  
|[Abort](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|非同期の式の評価を終了します。|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|この式を同期的に評価します。|  
  
## <a name="remarks"></a>Remarks  
 セッション デバッグ マネージャー (SDM) がへの呼び出しで DE からスタック フレームを取得するプログラムが停止されると、 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)します。 SDM を呼び出して[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)を取得する、 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)インターフェイス。 これがへの呼び出しに続く[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)を作成する、`IDebugExpression2`インターフェイスで、すぐに評価できる解析された式を表します。  
  
 SDM を呼び出すか[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)または[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)を実際には、式を評価し、値を生成します。  
  
 実装に`IDebugExpressionContext2::ParseText`、DE、COM を使用して`CoCreateInstance`式エバリュエーターをインスタンス化し、取得する関数、 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)インターフェイス (例を参照してください、`IDebugExpressionEvaluator`インターフェイス)。 デを呼び出して[解析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)を取得する、 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)インターフェイス。 実装では、このインターフェイスを使用してください。`IDebugExpression2::EvaluateSync`と`IDebugExpression2::EvaluateAsync`評価を実行します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)

