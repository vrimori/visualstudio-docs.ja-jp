---
title: 式エバリュエーターの実装 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d51762eb2d26c39eab5d803384adfed216e5bd89
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53882326"
---
# <a name="implement-an-expression-evaluator"></a>式エバリュエーターを実装します。
> [!IMPORTANT]
>  Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細については、次を参照してください。 [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 デバッグ エンジン (DE)、シンボル プロバイダー (SP)、バインダー オブジェクト、および、式エバリュエーター (EE) の間で複雑な相互作用は、式を評価します。 これら 4 つのコンポーネントは、1 つのコンポーネントによって実装され、別で使用されるインターフェイスで接続されます。  
  
 EE は、文字列の形式で DE から式を取得および解析または評価します。 EE には、次のインターフェイスは、DE によって使用されますが実行されます。  
  
- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
  EE は、シンボルとオブジェクトの値を取得する、DE、によって提供されるバインダー オブジェクトを呼び出します。 EE、DE によって実装される次のインターフェイスを使用します。  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
  EE 実行[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)します。 `IDebugProperty2` ローカル変数、プリミティブ型、型の適切な情報が表示されますが、Visual Studio のオブジェクトなど、式の評価の結果を記述するためのメカニズムを提供、**ローカル**、**ウォッチ**、または**イミディ エイト**ウィンドウ。  
  
  SP は、情報の入力を求められたらときに、DE、EE に付与されます。 SP は、アドレスと、次のインターフェイスおよびその派生物などのフィールドを記述するインターフェイスを実行します。  
  
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
  EE は、これらのインターフェイスのすべてを使用します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [式エバリュエーターの実装方法](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 式エバリュエーター (EE) の実装方法の 3 つの手順を定義します。  
  
## <a name="see-also"></a>関連項目  
 [CLR の式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)