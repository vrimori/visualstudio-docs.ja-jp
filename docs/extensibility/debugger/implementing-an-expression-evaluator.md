---
title: "式エバリュエーターを実装します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "式エバリュエーター"
  - "[デバッグ SDK] の式エバリュエーターのデバッグ"
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 式エバリュエーターを実装します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 デバッグ エンジン \(DE\)、シンボル プロバイダー \(SP\)、バインダー オブジェクトおよび式エバリュエーター \(EE\) 自体の間の複雑な相互作用は、式を評価します。 1 つのコンポーネントによって実装され、別の作業で使用するインターフェイスでは、これら 4 つのコンポーネントが接続されています。  
  
 EE は、式では、文字列の形式で DE から取得し、解析または評価します。 EE は、DE によって使用されて、次のインターフェイスを実装します。  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
 EE は、シンボルとオブジェクトの値を取得、DE によって提供される、バインダー オブジェクトを呼び出します。 EE は、デによって実装されている次のインターフェイスを使用します。  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
-   [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
-   [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
-   [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
-   [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
-   [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
 EE を実装して [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)します。`IDebugProperty2` ローカル変数、プリミティブ、または Visual Studio で、該当する情報を表示する、オブジェクトなど、式の評価の結果を記述するための機構を提供、 **ローカル**, 、**ウォッチ**, 、または **イミディ エイト** ウィンドウです。  
  
 SP は、詳細メッセージが表示されたら、DE、EE に付与されます。 SP には、アドレスと、次のインターフェイスと、そのなどのフィールドを記述するインターフェイスを実装します。  
  
-   [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
 EE は、これらのインターフェイスのすべてを使用します。  
  
## このセクションの内容  
 [式エバリュエーターの実装方法](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 式エバリュエーター \(EE\) の実装方法の 3 段階のプロセスを定義します。  
  
## 参照  
 [CLR 式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)