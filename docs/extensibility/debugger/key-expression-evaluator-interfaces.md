---
title: 式エバリュエーターのインターフェイスのキー |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fe0c592c65e2c6ab7429cef44a830325a834ecdc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="key-expression-evaluator-interfaces"></a>キー式エバリュエーター インターフェイス
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 評価のコンテキストと共に式エバリュエーター (EE) を記述する場合は、次のインターフェイスに慣れておく必要があります。  
  
## <a name="interface-descriptions"></a>インターフェイスの説明  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
     1 つのメソッドを持つ[GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md)実行の現在のポイントを表すデータ構造体を取得します。 このデータ構造体は、デバッグ エンジン (DE) が渡される 3 つの引数の 1 つ、 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)式を評価するメソッド。 このインターフェイスは通常、シンボル プロバイダーによって実装されます。  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
     [バインド](../../extensibility/debugger/reference/idebugbinder-bind.md)メソッドで、シンボルの現在の値が含まれるメモリ領域を取得します。 両方を含む、表されるメソッドで指定された、 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)オブジェクト、およびシンボル自体によって表される、 [IDebugField](../../extensibility/debugger/reference/idebugfield.md)オブジェクト、`IDebugBinder::Bind`記号の値を返します。 `IDebugBinder` 通常、DE によって実装されます。  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
     単純なデータ型を表します。 配列と、メソッドなどのより複雑な型を使用して、派生[IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md)と[IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md)インターフェイスをそれぞれします。 [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md)もう 1 つの重要な派生インターフェイス メソッドまたはクラスと同様に、その他の記号を含むシンボルを表すです。 `IDebugField`インターフェイス、およびその派生クラス) のシンボル プロバイダーにより実行されます。  
  
     `IDebugField`オブジェクトには、シンボルの種類と名前を見つけるために使用されると連携して、 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)オブジェクト、その値を検索するために使用できます。  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
     シンボルの実行時の値の実際のビットを表します。 [バインド](../../extensibility/debugger/reference/idebugbinder-bind.md)受け取り、 [IDebugField](../../extensibility/debugger/reference/idebugfield.md)オブジェクトでは、シンボルを表すを返します、 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)オブジェクト。 [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md)メソッドは、メモリ バッファーにシンボルの値を返します。 デは通常、メモリ内のプロパティの値を表すためには、このインターフェイスを実装します。  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
     このインターフェイスは、式エバリュエーター自体を表します。 重要なメソッドは[解析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)、返された、 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)インターフェイスです。  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
     このインターフェイスは、解析された式を評価する準備ができてを表します。 重要なメソッドは[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)値と式の型を表す IDebugProperty2 を返します。  
  
-   [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)  
  
     このインターフェイスは、値とその型を表す、式の評価の結果です。  
  
## <a name="see-also"></a>関連項目  
 [評価コンテキスト](../../extensibility/debugger/evaluation-context.md)