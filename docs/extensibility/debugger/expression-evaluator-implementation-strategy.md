---
title: "式エバリュエーターの実装方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "式の評価、実装戦略"
  - "デバッグ エンジンは、実装戦略"
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 式エバリュエーターの実装方法
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 式エバリュエーター \(EE\) を迅速に作成する方法の 1 つは、最初にローカル変数を表示するために必要な最小限のコードを実装する、 **ローカル** ウィンドウです。 理解すると便利です内の各行の **ローカル** 名、型、およびローカル変数の値にウィンドウが表示され、3 つすべてがによって表される、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) オブジェクトです。 名前、種類、およびローカル変数の値から取得できます、 `IDebugProperty2` を呼び出してオブジェクトその [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) メソッドです。 ローカル変数を表示する方法について、 **ローカル** ウィンドウを参照してください [\[ローカル\] を表示します。](../Topic/Displaying%20Locals.md)します。  
  
## 説明  
 可能な実装順序を実装するための開始 [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)します。[Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) と [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) メソッドを実装して、ローカル変数を表示する必要があります。 呼び出す `IDebugExpressionEvaluator::GetMethodProperty` を返します、 `IDebugProperty2` メソッドを表すオブジェクト。 つまり、、 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) オブジェクトです。 メソッド自体に表示されない、 **ローカル** ウィンドウです。  
  
 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) メソッドを次に実装する必要があります。 デバッグ エンジン \(DE\) を渡すことによって、ローカル変数と引数の一覧を取得するには、このメソッドを呼び出して `IDebugProperty2::EnumChildren` 、 `guidFilter` の引数 `guidFilterLocalsPlusArgs`します。`IDebugProperty2::EnumChildren` 呼び出し [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) と [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), が 1 つの列挙体に結果を結合します。 詳細については、「[\[ローカル\] を表示します。](../Topic/Displaying%20Locals.md)」を参照してください。  
  
## 参照  
 [式エバリュエーターを実装します。](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [\[ローカル\] を表示します。](../Topic/Displaying%20Locals.md)