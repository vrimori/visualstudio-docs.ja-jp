---
title: "式エバリュエーター |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 55aaa595c49d0c50cff5f874d1b322c3adbb9729
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="expression-evaluator"></a>式エバリュエーター
(EE) の式エバリュエーターでは、IDE が中断モードの場合、ユーザーを表示することを解析および実行時に、変数や式を評価するための言語の構文を確認します。  
  
## <a name="using-expression-evaluators"></a>式エバリュエーターを使用します。  
 使用して式を作成、 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)メソッドは、次のようにします。  
  
1.  デバッグ エンジン (DE) は、実装、 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)インターフェイスです。  
  
2.  デバッグ パッケージの取得、`IDebugExpressionContext2`オブジェクトから、 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)インターフェイスを呼び出し、続いて、`IDebugStackFrame2::ParseText`を得るためのメソッド、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)オブジェクト。  
  
3.  デバッグ パッケージ呼び出し、 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)メソッドまたは[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)式の値を取得します。 `IDebugExpression2::EvaluateAsync`コマンド/イミディ エイト ウィンドウから呼び出されます。 その他のすべての UI コンポーネントを呼び出す`IDebugExpression2::EvaluateSync`です。  
  
4.  式の評価の結果は、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)オブジェクトで、名前、型、および式の評価の結果の値が含まれています。  
  
 式の評価中に、EE にシンボル プロバイダー コンポーネントからの情報が必要です。 シンボル プロバイダーでは、識別して、解析された式を理解するために使用されるシンボル情報を提供します。  
  
 非同期の式の評価が完了したら、非同期イベントから送信されるセッションのデバッグ マネージャー (SDM) を通じて DE 式の評価が完了したことを IDE に通知します。 評価の結果がへの呼び出しから返される同期式の評価が完了したら、`IDebugExpression2::EvaluateSync`メソッドです。  
  
## <a name="implementation-notes"></a>実装に関するメモ  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]と共通言語ランタイム (CLR) インターフェイスを使用して、式エバリュエーターと対話するデバッグ エンジンが予想されます。 その結果、式エバリュエーターで動作する、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]デバッグ エンジンは、CLR をサポートする必要があります (すべての CLR デバッグ インターフェイスの完全な一覧は含まれて含まれている debugref.doc の[!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)])。  
  
## <a name="see-also"></a>参照  
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)