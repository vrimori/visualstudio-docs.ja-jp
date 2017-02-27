---
title: "キー式エバリュエーター インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[デバッグ SDK] の式の評価のデバッグ"
  - "式の評価、インターフェイス"
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# キー式エバリュエーター インターフェイス
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 評価コンテキストと共に式エバリュエーター \(EE\) を作成するときに、次のインターフェイスを理解しておく必要があります。  
  
## インターフェイスの説明  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
     1 つのメソッドを持つ [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), 、実行の現在のポイントを表すデータ構造体を取得します。 このデータ構造体は、デバッグ エンジン \(DE\) が渡される 3 つの引数の 1 つ、 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 式を評価するメソッドです。 このインターフェイスは通常、シンボル プロバイダーによって実装されます。  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
     [バインド](../../extensibility/debugger/reference/idebugbinder-bind.md) メソッドで、シンボルの現在の値を格納しているメモリ領域を取得します。 両方を含むが表すメソッドを与え、 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) オブジェクト、および記号自体によって表される、 [IDebugField](../../extensibility/debugger/reference/idebugfield.md) オブジェクト、 `IDebugBinder::Bind` 記号の値を返します。`IDebugBinder` 通常、DE によって実装されます。  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
     単純なデータ型を表します。 派生クラスを使用して配列やメソッドなどのより複雑な型の [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) と [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) インターフェイスをそれぞれします。[IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) メソッドまたはクラスのようなその他の記号を含む別の重要な派生インターフェイスを表す記号です。`IDebugField` インターフェイス \(とその派生物\) シンボル プロバイダーにより実行されます。  
  
     `IDebugField` オブジェクトでき、名前とシンボルの型を検索するために使用、と共に使用して、 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) オブジェクト、その値を検索に使用できることができます。  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
     シンボルの実行時の値の実際のビットを表します。[バインド](../../extensibility/debugger/reference/idebugbinder-bind.md)[IDebugField](../../extensibility/debugger/reference/idebugfield.md) 、シンボルを表すを返す、オブジェクト、 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) オブジェクトです。[GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) メソッドは、メモリ バッファーにシンボルの値を返します。 デは、通常、メモリ内のプロパティの値を表すためには、このインターフェイスを実装します。  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
     このインターフェイスは、式エバリュエーター自体を表します。 重要なメソッドは [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), 、これによって、 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) インターフェイスです。  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
     このインターフェイスは、評価する準備が解析された式を表します。 重要なメソッドは [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 値と式の型を表す IDebugProperty2 を返します。  
  
-   [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)  
  
     このインターフェイスは、値とその型を表す、式の評価の結果です。  
  
## 参照  
 [評価コンテキスト](../../extensibility/debugger/evaluation-context.md)