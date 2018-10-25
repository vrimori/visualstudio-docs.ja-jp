---
title: IDebugStackFrame2::GetExpressionContext |Microsoft Docs
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
- IDebugStackFrame2::GetExpressionContext
helpviewer_keywords:
- IDebugStackFrame2::GetExpressionContext
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: be81a74f9ce13511e463c4244fc1e817f5c94d1d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940633"
---
# <a name="idebugstackframe2getexpressioncontext"></a>IDebugStackFrame2::GetExpressionContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

スタック フレームとスレッドの現在のコンテキストで式の評価の評価コンテキストを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetExpressionContext (   
   IDebugExpressionContext2** ppExprCxt  
);  
```  
  
```csharp  
int GetExpressionContext (   
   out IDebugExpressionContext2 ppExprCxt  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppExprCxt`  
 [out]返します、 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)式の評価のコンテキストを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 一般に、式の評価コンテキストは、式の評価を実行するためのスコープとして考えることができます。 呼び出す、 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)式を解析し、結果を呼び出すメソッド[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)または[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)解析された式を評価するメソッド。  
  
## <a name="see-also"></a>関連項目  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)

