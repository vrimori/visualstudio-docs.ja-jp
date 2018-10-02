---
title: 式の評価 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c51cc08da8c71a2ac1f25d02461ea9c24797ebc3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544295"
---
# <a name="evaluating-expressions"></a>評価式
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[を評価する式](https://docs.microsoft.com/visualstudio/extensibility/debugger/evaluating-expressions)します。  
  
式は、自動変数、ウォッチ、クイック ウォッチ、またはイミディ エイト ウィンドウから下へ渡された文字列から作成されます。 式が評価され、変数または引数とその値の型と名前を含む印刷文字列が生成されます。 この文字列は、対応する IDE ウィンドウに表示されます。  
  
## <a name="implementation"></a>実装  
 プログラムがブレークポイントで停止した場合、式が評価されます。 式自体はによって表される、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)インターフェイスでは、解析された式をバインドし、指定された式の評価のコンテキスト内で評価できるように準備を表します。 スタック フレーム (DE) デバッグ エンジンを実装することで提供する式の評価コンテキストの決定、 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)インターフェイス。  
  
 ユーザー文字列の指定と[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)インターフェイス、デバッグ エンジン (DE) を取得できます、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)インターフェイス ユーザー文字列を渡すことによって、 [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)メソッド。 返される IDebugExpression2 インターフェイスには、評価のための準備が解析された式が含まれています。  
  
 `IDebugExpression2` 、インターフェイス、DE は同期または非同期の式の評価を式の値を取得できますを使用して[IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)または[IDebugExpression2:。EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)します。 変数または引数の型と名前と共に、この値は、表示するため、IDE に送信されます。 値、名前、型がで表される、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)インターフェイス。  
  
 式の評価を有効にする、DE を実装する必要があります、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)と[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)インターフェイス。 同期および非同期の評価の実装が必要に、 [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)メソッド。  
  
## <a name="see-also"></a>関連項目  
 [スタック フレーム](../../extensibility/debugger/stack-frames.md)   
 [式の評価コンテキスト](../../extensibility/debugger/expression-evaluation-context.md)   
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)

