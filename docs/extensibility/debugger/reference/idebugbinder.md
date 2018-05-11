---
title: IDebugBinder |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3514d280b6718fc670f3bdac35b6bbacbbf2b09c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 このインターフェイスは、通常プロバイダーによって返される、記号、メモリ コンテキストまたはシンボルの現在の値を格納しているオブジェクトをシンボルのフィールドをバインドします。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugBinder : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 このインターフェイスは、式の評価をサポートし、デバッグ エンジン (DE) によって実装する必要があります。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスは式の評価プロセスに使用し、通常の実装では使用[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)と[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)です。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugBinder`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[バインド](../../../extensibility/debugger/reference/idebugbinder-bind.md)|メモリ コンテキストまたはシンボルの現在の値を格納しているオブジェクトを取得します。|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|オブジェクトの実行時の型を決定します。|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|メモリ コンテキスト オブジェクトの場所またはメモリ アドレスに変換します。|  
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|取得、 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)関数のパラメーターを作成するために使用します。|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|変数の正確な型を取得します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスでの式エバリュエーターで使用されるオブジェクト ツリーの解析を返します。 式エバリュエーターが式内のシンボルのインスタンスに変換するシンボル プロバイダーを使用して式を解析して[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)、その型と、ソース コード内の場所の観点から各シンボルを記述します。 [バインド](../../../extensibility/debugger/reference/idebugbinder-bind.md)メソッドに変換`IDebugField`オブジェクトを[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)接続またはシンボルをバインドするオブジェクトをメモリ内の実際の値を入力します。 これら`IDebugObject`オブジェクトは、後で評価の解析ツリーに保存されます。  
  
## <a name="requirements"></a>要件  
 ヘッダー: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [式の評価インターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)