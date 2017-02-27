---
title: "式エバリュエーターのアーキテクチャ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アーキテクチャでは、式エバリュエーター"
  - "式エバリュエーターでは、アーキテクチャ"
  - "[デバッグ SDK] の式エバリュエーターのデバッグ"
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 式エバリュエーターのアーキテクチャ
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 Visual Studio のデバッグ パッケージへの独自の言語での統合は、必要な式エバリュエーター \(EE\) インターフェイスを実装して、共通言語ランタイムのシンボル プロバイダー \(SP\) およびバインダー インターフェイスを呼び出すことを意味します。 SP とバインダー オブジェクトの現在の実行のアドレスとは、式が評価されるコンテキストです。 これらのインターフェイスの生成し、利用される情報は、EE のアーキテクチャの主な概念を表します。  
  
## 概要  
  
### 式を解析  
 プログラムをデバッグするときは、さまざまな理由が、常に \(ユーザーが挿入したブレークポイントまたは例外の原因となった 1 つ\) のブレークポイントでデバッグするプログラムが停止された場合の式が評価されます。 表される Visual Studio でのスタック フレームを取得するときにこの時点では、 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) デバッグ エンジン \(DE\) からのインターフェイスです。 Visual Studio を呼び出して [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) させることが、 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) インターフェイスです。 このインターフェイスを表すコンテキストで式を評価できます。 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 評価プロセスに対するエントリ ポイントです。 この時点までは、すべてのインターフェイスは、DE によって実装されます。  
  
 `IDebugExpressionContext2::ParseText` が呼び出されると、DE はブレークポイントが発生したソース ファイルの言語に関連付けられている EE をインスタンス化 \(デもをインスタンス化、SH この時点で\)。 EE はによって表される、 [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) インターフェイスです。 デを呼び出して [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) の評価を準備する \(テキスト形式\) の式を解析された式に変換します。 この解析の式がによって表される、 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) インターフェイスです。 式が通常解析され、この時点で評価されないことに注意してください。  
  
 デを実装するオブジェクトの作成、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) インターフェイス、put、 `IDebugParsedExpression` オブジェクトを `IDebugExpression2` オブジェクトを返します、 `IDebugExpression2` オブジェクトから `IDebugExpressionContext2::ParseText`します。  
  
### 式を評価します。  
 Visual Studio はいずれかを呼び出して [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) または [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 解析された式を評価します。 これら両方のメソッドを呼び出す [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) \(`IDebugExpression2::EvaluateSync` メソッドを呼び出すときに、すぐに `IDebugExpression2::EvaluateAsync` バック グラウンド スレッドでメソッドを呼び出します\) を解析された式を評価して返す、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 値と解析された式の型を表すインターフェイスです。`IDebugParsedExpression::EvaluateSync` によって表される、実際の値に解析された式を変換するには指定された SH、アドレスとバインダー、 `IDebugProperty2` インターフェイスです。  
  
### たとえば  
 ユーザーが内の変数の表示を実行中のプログラムで、ブレークポイントにヒットした後、 **\[クイック ウォッチ\]** \] ダイアログ ボックス。 このダイアログ ボックスでは、変数の名前、その値、およびその型を示します。 ユーザーは、値を変更通常ことができます。  
  
 ときに、 **\[クイック ウォッチ\]** \] ダイアログ ボックスが表示される、検査されている変数の名前がテキストとして送信される [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)します。 返されます。、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) ここでは、解析された式を表すオブジェクトでは、変数です。[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 呼び出して生成し、 `IDebugProperty2` 変数の値の種類とその名前を表すオブジェクト。 表示されるこの情報になります。  
  
 ユーザーは、変数の値を変更した場合 [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) プログラムを再開したときに使用されますので、メモリ内の変数の値を変更する新しい値で呼び出された実行します。  
  
 参照してください [\[ローカル\] を表示します。](../Topic/Displaying%20Locals.md) の変数の値を表示するには、このプロセスの詳細についてです。 参照してください [ローカルの値を変更します。](../../extensibility/debugger/changing-the-value-of-a-local.md) 変数の値を変更する方法の詳細についてです。  
  
## このセクションの内容  
 [評価コンテキスト](../../extensibility/debugger/evaluation-context.md)  
 デ EE を呼び出すときに渡される引数を提供します。  
  
 [キー式エバリュエーター インターフェイス](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 評価コンテキストと共に、EE を記述するときに必要な重要なインターフェイスについて説明します。  
  
## 参照  
 [CLR 式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [\[ローカル\] を表示します。](../Topic/Displaying%20Locals.md)   
 [ローカルの値を変更します。](../../extensibility/debugger/changing-the-value-of-a-local.md)