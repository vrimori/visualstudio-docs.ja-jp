---
title: 式エバリュエーター |Microsoft Docs
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
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2d5ad6c3c97fc88ef938caaccad1627dbc5859c2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911909"
---
# <a name="expression-evaluator"></a>式エバリュエーター
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

(EE) の式エバリュエーターでは、IDE が中断モードの場合、ユーザーが表示できるように解析および実行時に、変数と式を評価する言語の構文を確認します。  
  
## <a name="using-expression-evaluators"></a>式エバリュエーターを使用します。  
 使用して式を作成、 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)メソッドは、次のようにします。  
  
1. デバッグ エンジン (DE) を実装して、 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)インターフェイス。  
  
2. デバッグ パッケージを取得、`IDebugExpressionContext2`オブジェクトから、 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)インターフェイスに呼び出し、`IDebugStackFrame2::ParseText`を取得するメソッド、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)オブジェクト。  
  
3. デバッグ パッケージの呼び出し、 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)メソッドまたは[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)式の値を取得します。 `IDebugExpression2::EvaluateAsync` コマンド/イミディ エイト ウィンドウから呼び出されます。 その他のすべての UI コンポーネントを呼び出す`IDebugExpression2::EvaluateSync`します。  
  
4. 式の評価の結果は、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)オブジェクトで、名前、種類、および式の評価の結果の値が含まれています。  
  
   式の評価中に、EE にシンボル プロバイダー コンポーネントからの情報が必要です。 シンボル プロバイダーでは、識別し、解析された式を理解するために使用するシンボリック情報を提供します。  
  
   非同期式の評価が完了したら、非同期のイベントは、式の評価が完了したことを IDE に通知する、DE セッション デバッグ マネージャー (SDM) 経由で送信されます。 評価の結果がへの呼び出しから返される同期式の評価が完了すると、`IDebugExpression2::EvaluateSync`メソッド。  
  
## <a name="implementation-notes"></a>実装に関する注意事項  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]デバッグ エンジンが共通言語ランタイム (CLR) のインターフェイスを使用して、式エバリュエーターと対話する予定です。 その結果、式エバリュエーターと連動する、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]デバッグ エンジンは、CLR をサポートする必要があります (一部である、debugref.doc で見つかるすべての CLR デバッグのインターフェイスの完全な一覧の[!INCLUDE[winsdklong](../../includes/winsdklong-md.md)])。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)

