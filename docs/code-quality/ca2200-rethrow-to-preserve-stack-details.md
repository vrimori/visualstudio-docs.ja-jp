---
title: 'Ca 2200: スタックの詳細を保持するために Rethrow |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 18fe55136ca501974b33a04513905ff17fe19748
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: スタック詳細を保持するために再度スローします
|||  
|-|-|  
|TypeName|RethrowToPreserveStackDetails|  
|CheckId|CA2200|  
|カテゴリ|Microsoft.Usage|  
|互換性に影響する変更点|中断なし|  
  
## <a name="cause"></a>原因  
 例外が再スローされ、例外がで明示的に指定、`throw`ステートメントです。  
  
## <a name="rule-description"></a>規則の説明  
 例外がスローされると、伝達される情報の一部は、スタック トレースです。 スタック トレースは、例外をスローし、例外をキャッチするメソッドを使用して終了するメソッドで始まるメソッドの呼び出し階層の一覧を示します。 例外を指定することによって、例外がスローされます再、`throw`ステートメントでは、スタック トレースは、現在のメソッドに再起動し、例外をスローした元のメソッドと、現在のメソッド間のメソッド呼び出しの一覧は失われます。 例外には、元のスタック トレース情報を保持するを使用して、`throw`例外を指定しないでステートメントです。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、例外を明示的に指定せず、例外を再スローします。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 次の例では、メソッド、 `CatchAndRethrowExplicitly`、ルールと、メソッドに違反して`CatchAndRethrowImplicitly`規則に適合します。  
  
 [!code-csharp[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/CSharp/ca2200-rethrow-to-preserve-stack-details_1.cs)]
 [!code-vb[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/VisualBasic/ca2200-rethrow-to-preserve-stack-details_1.vb)]