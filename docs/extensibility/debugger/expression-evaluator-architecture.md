---
title: "式エバリュエーター アーキテクチャ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6805b97da8e8f742b1b6c0bb3298e9324bb1f72e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="expression-evaluator-architecture"></a>式エバリュエーターのアーキテクチャ
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 必要な式エバリュエーター (EE) インターフェイスを実装して、共通言語ランタイムのシンボル プロバイダー (SP) およびバインダー インターフェイスを呼び出すことを Visual Studio デバッグ パッケージに独自の言語を統合することを意味します。 現在の実行のアドレスと共にの SP およびバインダー オブジェクトは、式が評価されるコンテキストがします。 これらのインターフェイスを作成および使用する情報は、EE のアーキテクチャの主な概念を表します。  
  
## <a name="overview"></a>概要  
  
### <a name="parsing-the-expression"></a>式の解析  
 プログラムをデバッグするときは、さまざまな理由が、常にブレークポイント (ユーザーが挿入したブレークポイントまたは例外の原因となったいずれか) でデバッグするプログラムが停止したときの式が評価されます。 によって表されるように Visual Studio でのスタック フレームを取得するときにこの時点では、 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)デバッグ エンジン (DE) からのインターフェイスです。 Visual Studio は、呼び出す[GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)を取得する、 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)インターフェイスです。 このインターフェイスは、式を評価できる; コンテキストを表します[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)評価プロセスに対するエントリ ポイントです。 このポイントまですべてのインターフェイスは、DE によって実装されます。  
  
 ときに`IDebugExpressionContext2::ParseText`が呼び出されると、DE をインスタンス化が、ブレークポイントが発生したソース ファイルの言語に関連付けられている EE (デもをインスタンス化、SH この時点で)。 EE で表される、 [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)インターフェイスです。 DE を呼び出して[解析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)(テキスト形式) の式を解析された式に変換する評価の準備が完了します。 この解析済み表現で表される、 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)インターフェイスです。 式が通常解析され、この時点で評価されないことに注意してください。  
  
 デを実装するオブジェクトを作成する、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)インターフェイス、配置、`IDebugParsedExpression`オブジェクトに、`IDebugExpression2`オブジェクト、および返します、`IDebugExpression2`オブジェクトから`IDebugExpressionContext2::ParseText`です。  
  
### <a name="evaluating-the-expression"></a>式の評価  
 Visual Studio はいずれかを呼び出して[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)または[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)解析された式を評価します。 これら両方のメソッドを呼び出す[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (`IDebugExpression2::EvaluateSync`メソッドを呼び出すときに、すぐに`IDebugExpression2::EvaluateAsync`はバック グラウンド スレッドからメソッドを呼び出します) を解析された式を評価し、返す、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)値と解析された式の型を表すインターフェイスです。 `IDebugParsedExpression::EvaluateSync`によって表される、実際の値に解析された式を変換では指定された SH、アドレス、およびバインダー、`IDebugProperty2`インターフェイスです。  
  
### <a name="for-example"></a>例えば  
 ユーザーが内の変数の表示を実行中のプログラムで、ブレークポイントにヒットした後、 **クイック ウォッチ**  ダイアログ ボックス。 このダイアログ ボックスでは、変数の名前、その値、およびその型を示します。 ユーザーは、値を変更通常ことができます。  
  
 ときに、 **[クイック ウォッチ]**  ダイアログ ボックスが表示されると、検査されている変数の名前がテキストとして送信[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)です。 これを返します、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)ここでは、解析された式を表すオブジェクトでは、変数です。 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)が生成するために呼び出されます、`IDebugProperty2`変数の値の種類とその名前を表すオブジェクト。 この情報が表示されます。  
  
 ユーザーが変数の値を変更した場合[SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)新しいプログラムを再開したときに使用されますので、メモリ内の変数の値を変更します。 値を使用して呼び出したを実行しています。  
  
 参照してください[を表示するローカル](../../extensibility/debugger/displaying-locals.md)変数の値を表示するには、このプロセスの詳細についてはします。 参照してください[ローカルの値を変更する](../../extensibility/debugger/changing-the-value-of-a-local.md)変数の値を変更する方法の詳細についてはします。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [評価コンテキスト](../../extensibility/debugger/evaluation-context.md)  
 デ EE を呼び出すときに渡される引数を提供します。  
  
 [主要なエバリュエーター インターフェイス](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 評価のコンテキストと共に、EE を記述する場合に必要な重要なインターフェイスについて説明します。  
  
## <a name="see-also"></a>関連項目  
 [CLR 式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [ローカル変数を表示します。](../../extensibility/debugger/displaying-locals.md)   
 [ローカルの値の変更](../../extensibility/debugger/changing-the-value-of-a-local.md)