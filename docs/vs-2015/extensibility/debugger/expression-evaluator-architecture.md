---
title: 式エバリュエーターのアーキテクチャ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7b461a6ebf7b7fa1b6e35f49b1c25d6422277d0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49196301"
---
# <a name="expression-evaluator-architecture"></a>式エバリュエーターのアーキテクチャ
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 Visual Studio のデバッグ パッケージへの独自の言語での統合は、必要な式エバリュエーター (EE) のインターフェイスを実装して、共通言語ランタイムのシンボル プロバイダー (SP) とバインダー インターフェイスを呼び出すことを意味します。 現在の実行のアドレスと共に、SP とバインダー オブジェクトは、式が評価されるコンテキストです。 これらのインターフェイスの生成および消費する情報は、EE のアーキテクチャの主な概念を表します。  
  
## <a name="overview"></a>概要  
  
### <a name="parsing-the-expression"></a>式の解析  
 プログラムをデバッグするときにさまざまな理由が常にデバッグ中のプログラム (ブレークポイント、ユーザーが配置またはいずれかの例外の原因となった)、ブレークポイントで停止されたときの式が評価されます。 によって表される Visual Studio でのスタック フレームを取得するときに、この時点では、 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)デバッグ エンジン (DE) からのインターフェイス。 Visual Studio を呼び出して[GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)を取得する、 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)インターフェイス。 このインターフェイスは、式を評価できます。 コンテキストを表します[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)評価プロセスにエントリ ポイントです。 ここまでは、すべてのインターフェイスは、DE によって実装されます。  
  
 ときに`IDebugExpressionContext2::ParseText`はブレークポイントが発生したソース ファイルの言語に関連付けられた EE 呼び出されると、インスタンス化、DE (デのインスタンス化も、SH この時点で)。 によって表される、EE、 [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)インターフェイス。 デを呼び出して[解析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)評価の準備が完了 (テキスト形式) の式を解析された式に変換します。 この解析された式がによって表される、 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)インターフェイス。 式が通常解析され、この時点で評価されないことに注意してください。  
  
 デを実装するオブジェクトを作成する、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)インターフェイス、put、`IDebugParsedExpression`オブジェクトを`IDebugExpression2`、オブジェクトを返します、`IDebugExpression2`オブジェクトから`IDebugExpressionContext2::ParseText`します。  
  
### <a name="evaluating-the-expression"></a>式を評価します。  
 Visual Studio はいずれかを呼び出して[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)または[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)解析された式を評価します。 これら両方のメソッドを呼び出す[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (`IDebugExpression2::EvaluateSync`メソッドを呼び出し中に、すぐに`IDebugExpression2::EvaluateAsync`はバック グラウンド スレッドからメソッドを呼び出します) を解析された式を評価し、返す、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)解析された式の種類と値を表すインターフェイスです。 `IDebugParsedExpression::EvaluateSync` 解析された式で表される、実際の値に変換するには、指定された SH、アドレスとバインダー、`IDebugProperty2`インターフェイス。  
  
### <a name="for-example"></a>例えば  
 ユーザーが内の変数を表示するが、実行中のプログラムで、ブレークポイントにヒットした後、 **クイック ウォッチ**  ダイアログ ボックス。 このダイアログ ボックスには、変数の名前、その値、およびその型が表示されます。 ユーザーは、値を通常変更できます。  
  
 ときに、 **[クイック ウォッチ]**  ダイアログ ボックスが表示される、調べている変数の名前をテキストとして送信されます[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)します。 これにより返されます、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)ここでは、解析された式を表すオブジェクトは、変数。 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)生成するために呼び出されますが、`IDebugProperty2`変数の値と型、ほかの名前を表すオブジェクト。 表示されるこの情報になります。  
  
 ユーザーは、変数の値を変更した場合[SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)プログラムを再開したときに使用されますので、メモリ内の変数の値を変更する、新しい値を使用して呼び出したを実行します。  
  
 参照してください[を表示するローカル](../../extensibility/debugger/displaying-locals.md)変数の値を表示するには、このプロセスの詳細についてはします。 参照してください[ローカルの値を変更する](../../extensibility/debugger/changing-the-value-of-a-local.md)変数の値を変更する方法の詳細についてはします。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [評価コンテキスト](../../extensibility/debugger/evaluation-context.md)  
 DE、EE を呼び出すときに渡される引数を提供します。  
  
 [主要なエバリュエーター インターフェイス](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 評価コンテキストと共に、EE を記述するときに必要な重要なインターフェイスについて説明します。  
  
## <a name="see-also"></a>関連項目  
 [CLR の式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [ローカルの表示](../../extensibility/debugger/displaying-locals.md)   
 [ローカルの値の変更](../../extensibility/debugger/changing-the-value-of-a-local.md)

