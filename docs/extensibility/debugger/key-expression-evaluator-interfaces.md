---
title: 式エバリュエーター インターフェイスのキー |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 060656c10c8f516681a459153621ad1dd2d72ee0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55026210"
---
# <a name="key-expression-evaluator-interfaces"></a>主要なエバリュエーター インターフェイス
> [!IMPORTANT]
>  Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 評価コンテキストと共に、式エバリュエーター (EE) を記述する場合は、次のインターフェイスに慣れておく必要があります。  
  
## <a name="interface-descriptions"></a>インターフェイスの説明  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
     1 つのメソッドを持つ[GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md)実行の現在のポイントを表すデータ構造体を取得します。 このデータ構造は、デバッグ エンジン (DE) からに渡される 3 つの引数の 1 つ、 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)式を評価するメソッド。 このインターフェイスは通常、シンボル プロバイダーによって実装されます。  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
     [バインド](../../extensibility/debugger/reference/idebugbinder-bind.md)メソッドで、シンボルの現在の値を格納しているメモリ領域を取得します。 両方のコンテナー、によって表されるメソッドの指定、 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)オブジェクト、および記号自体によって表される、 [IDebugField](../../extensibility/debugger/reference/idebugfield.md)オブジェクト、`IDebugBinder::Bind`シンボルの値を返します。 `IDebugBinder` 通常、DE によって実装されます。  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
     単純なデータ型を表します。 派生クラスを使用して配列やメソッドなどのより複雑な型の[IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md)と[IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md)インターフェイスをそれぞれします。 [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md)メソッドやクラスなどの他のシンボルを含むシンボルを表すもう 1 つの重要な派生インターフェイスです。 `IDebugField`インターフェイス (とその派生物) は、通常シンボル プロバイダーによって実装されます。  
  
     `IDebugField`シンボルの型と名前を検索するために使用し、と共にオブジェクトを指定できます、 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)オブジェクト、その値を検索するために使用できます。  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
     シンボルの実行時の値の実際のビットを表します。 [バインド](../../extensibility/debugger/reference/idebugbinder-bind.md)は、 [IDebugField](../../extensibility/debugger/reference/idebugfield.md)オブジェクトをシンボルを表します。 を返します、 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)オブジェクト。 [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md)メソッドは、メモリ バッファーにシンボルの値を返します。 DE 通常メモリのプロパティの値を表すためには、このインターフェイスを実装します。  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
     このインターフェイスは、式エバリュエーター自体を表します。 重要なメソッドは[解析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)、返された、 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)インターフェイス。  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
     このインターフェイスは、すぐに評価できる解析された式を表します。 重要なメソッドは[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)どの値と式の型を表す IDebugProperty2 を返します。  
  
-   [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)  
  
     このインターフェイスとその型の値を表す、式の評価の結果です。  
  
## <a name="see-also"></a>関連項目  
 [評価コンテキスト](../../extensibility/debugger/evaluation-context.md)