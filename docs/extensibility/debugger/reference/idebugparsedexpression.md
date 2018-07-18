---
title: IDebugParsedExpression |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugParsedExpression
helpviewer_keywords:
- IDebugParsedExpression interface
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8b877dd974a0b96a176b54f308a6317e7324b6ab
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122315"
---
# <a name="idebugparsedexpression"></a>IDebugParsedExpression
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 このインターフェイスは、解析された式を評価する準備ができてを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugParsedExpression : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 式エバリュエーターでは、評価の準備が整った解析された式を表すためには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出し[解析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)このインターフェイスを返します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugParsedExpression`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|解析された式を評価します。|  
  
## <a name="remarks"></a>コメント  
 これを呼び出す呼び出し元の式を評価する準備ができたら[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)を返す、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)評価の結果を格納しています。 この 2 部構成方法の評価中、複数回評価されるように解析された式を有効にし、解析、式を解析の時間のかかる処理をバイパスして、評価します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [解析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)