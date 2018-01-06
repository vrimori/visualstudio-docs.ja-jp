---
title: "[ウォッチ] ウィンドウの式を評価する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fb109fd91e4c295bf372b14e26bc2a75c3be6b1d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="evaluating-a-watch-window-expression"></a>[ウォッチ] ウィンドウの式を評価します。
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 実行は一時停止、Visual Studio はデバッグ エンジンのウォッチ式のリスト内の各式の現在の値を確認するには、(DE) を呼び出します。 デは式エバリュエーター (EE) を使用して各式を評価し、Visual Studio にはその値を表示する、**ウォッチ**ウィンドウです。  
  
 ウォッチ式のリストの式が評価される方法の概要を次に示します。  
  
1.  Visual Studio は、DE を呼び出して[GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)を式の評価に使用できる式のコンテキストを取得します。  
  
2.  Visual Studio を呼び出し、ウォッチ式のリスト内の各式[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)式のテキストを解析された式に変換します。  
  
3.  `IDebugExpressionContext2::ParseText`呼び出し[解析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)を実際の生成とテキストの解析中の作業を行うには、 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)オブジェクト。  
  
4.  `IDebugExpressionContext2::ParseText`作成、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)オブジェクトと配置、`IDebugParsedExpression`にオブジェクト。 このすれば`DebugExpression2`オブジェクトは Visual Studio に返されます。  
  
5.  Visual Studio 呼び出し[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)解析された式を評価します。  
  
6.  `IDebugExpression2::EvaluateSync`呼び出しを渡す[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)を実際の評価を行い、生成、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Visual Studio に返されるオブジェクト。  
  
7.  Visual Studio 呼び出し[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)ウォッチ式の一覧に表示される、式の値を取得します。  
  
## <a name="parse-then-evaluate"></a>解析し、評価  
 複雑な式の解析は、それを評価するよりもかなり長くかかることができます、ため、式の評価プロセスは分割 2 つの手順: 1)、式を解析し、2) 解析された式を評価します。 これにより、評価発生回数が多しますが、式が 1 回だけを解析する必要があります。 中間の解析された式で EE から返される、 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)次々 にカプセル化され、として DE から返されたオブジェクト、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)オブジェクト。 `IDebugExpression`オブジェクトにすべての評価の延期、`IDebugParsedExpression`オブジェクト。  
  
> [!NOTE]
>  Visual Studio を前提としています。 この場合でも、この 2 段階のプロセスに従う、EE 必要はありません。EE は解析し、同じ手順で評価されるときに[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)は呼び出されます (これは MyCEE サンプルのしくみなど)。 場合は、言語には、複雑な式を形成できます、評価ステップから解析ステップを分割することがあります。 多くのウォッチ式、Visual Studio デバッガーでのパフォーマンスを向上このことができますが表示されています。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [式の評価の実装のサンプル](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 式の評価プロセスの手順に MyCEE サンプルを使用します。  
  
 [ウォッチ式の評価](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 成功した式の解析後の動作について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [評価コンテキスト](../../extensibility/debugger/evaluation-context.md)  
 デバッグ エンジン (DE) は、式エバリュエーター (EE) を呼び出すときに渡される引数を提供します。  
  
## <a name="see-also"></a>参照  
 [CLR 式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)