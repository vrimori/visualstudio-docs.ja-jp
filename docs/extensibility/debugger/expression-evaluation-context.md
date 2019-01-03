---
title: 式の評価コンテキスト |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 15b7f53dddefa78ef58818d20b5ca6eafb84e207
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835738"
---
# <a name="expression-evaluation-context"></a>式の評価コンテキスト
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 、デバッグ、**式の評価コンテキスト**:  
  
-   式の評価のコンテキストを表します。 一般に、評価コンテキストは、変数、パラメーター、関数、およびメソッドを評価する構文のスコープに対応します。 たとえば、スタック フレームに関連付けられている式の評価コンテキスト (該当する) 場合は、ローカル変数、メソッド パラメーター、およびクラス メンバーを評価するため、コンテキストが提供されます。  
  
-   プログラムがブレークポイントで停止したときに存在します。 式自体は、バインドと、指定されたコンテキストで評価の準備が整った解析された式を表すデータ構造です。  
  
     詳細については、式を使用して作成、 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)メソッド。 式を評価するときに、変数または引数とその値の型と名前を格納している印刷可能な文字列を生成します。 この文字列は、[ウォッチ] ウィンドウまたは IDE の [ローカル] ウィンドウに表示されます。  
  
     指定された、`BSTR`と[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)インターフェイス、デバッグ エンジン (DE) を作成できます、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)式を解析してインターフェイス。 指定された、`IDebugExpression2`インターフェイス、DE は同期または非同期の式の評価での値を取得できます。 変数または引数の型と名前と共に、この値は、表示するため、IDE に送信されます。  
  
## <a name="see-also"></a>関連項目  
 [式の評価のインターフェイス](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)