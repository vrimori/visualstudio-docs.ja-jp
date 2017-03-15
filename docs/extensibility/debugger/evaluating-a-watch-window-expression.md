---
title: "[ウォッチ] ウィンドウの式を評価します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ウォッチ ウィンドウの式"
  - "[ウォッチ] ウィンドウの式"
  - "式の評価、ウォッチ ウィンドウの式"
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# [ウォッチ] ウィンドウの式を評価します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 実行が一時停止、Visual Studio はデバッグ エンジンのウォッチ リスト内の各式の現在の値を確認するには、\(DE\) を呼び出します。 デは、式エバリュエーター \(EE\) を使用して各式を評価し、Visual Studio は内の値を表示、 **ウォッチ** ウィンドウです。  
  
 ウォッチ リストの式を評価する方法の概要を次に示します。  
  
1.  Visual Studio は、DE を呼び出して [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 式の評価に使用できる式のコンテキストを取得します。  
  
2.  Visual Studio の呼び出し、ウォッチ リスト内の各式 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 式のテキストを解析された式に変換します。  
  
3.  `IDebugExpressionContext2::ParseText` 呼び出し [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) を実際の生成とテキストの解析作業を行うには、 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) オブジェクトです。  
  
4.  `IDebugExpressionContext2::ParseText` 作成、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) オブジェクトと配置、 `IDebugParsedExpression` オブジェクトにします。 このは`DebugExpression2` Visual Studio にオブジェクトが返されます。  
  
5.  Visual Studio 呼び出し [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 解析された式を評価します。  
  
6.  `IDebugExpression2::EvaluateSync` 呼び出しに渡します [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) を実際の評価を行い、生成、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Visual Studio に返されるオブジェクト。  
  
7.  Visual Studio 呼び出し [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) ウォッチ リストに表示される式の値を取得します。  
  
## 解析し、評価  
 式を評価するプロセスは 2 つのステップに分割しているため、複雑な式の解析は、それを評価するよりもかなり長くかかることが: 1\) 式を解析し、2\)、解析された式を評価します。 これにより、評価発生回数しますが、式が 1 回だけを解析する必要があります。 EE にから中間の解析された式が返される、 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) を次々 にカプセル化され、として DE から返されたオブジェクト、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) オブジェクトです。`IDebugExpression` オブジェクトへのすべての評価の延期、 `IDebugParsedExpression` オブジェクトです。  
  
> [!NOTE]
>  EE 場合でも、Visual Studio ではこの機能は、この 2 段階のプロセスに準拠する必要はありません。EE は解析し、同じ手順で評価と [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) が呼び出されます \(これが MyCEE サンプルの動作など\)。 言語には、複雑な式を形成するの場合は、評価手順から解析ステップを分離します。 多くのウォッチ式と Visual Studio デバッガーでパフォーマンスが向上が表示されています。  
  
## このセクションの内容  
 [式の評価の実装のサンプル](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 MyCEE サンプルを使用して、式の評価プロセスの手順をします。  
  
 [\[ウォッチ式を評価します。](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 正常な式の解析した後の動作について説明します。  
  
## 関連項目  
 [評価コンテキスト](../../extensibility/debugger/evaluation-context.md)  
 デバッグ エンジン \(DE\) は、式エバリュエーター \(EE\) を呼び出すときに渡される引数を提供します。  
  
## 参照  
 [CLR 式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)