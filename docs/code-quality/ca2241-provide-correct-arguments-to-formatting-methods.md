---
title: ': Ca 2241 正しい引数を書式指定メソッドに |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a4fbaaa9b2d89b80fec1fb5106e94a7ef504e3c1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: 正しい引数を書式指定メソッドに指定します
|||  
|-|-|  
|TypeName|ProvideCorrectArgumentsToFormattingMethods|  
|CheckId|CA2241|  
|カテゴリ|Microsoft.Usage|  
|互換性に影響する変更点|中断なし|  
  
## <a name="cause"></a>原因  
 `format`などのメソッドに渡される引数を文字列<xref:System.Console.WriteLine%2A>、 <xref:System.Console.Write%2A>、または<xref:System.String.Format%2A?displayProperty=fullName>に各オブジェクトの引数、またはその逆を対応する書式指定項目が含まれていません。  
  
## <a name="rule-description"></a>規則の説明  
 などのメソッドの引数<xref:System.Console.WriteLine%2A>、 <xref:System.Console.Write%2A>、および<xref:System.String.Format%2A>の後にいくつかの書式指定文字列で構成されている<xref:System.Object?displayProperty=fullName>インスタンス。 書式指定文字列はテキストと、フォームの埋め込みの書式指定項目 {インデックス [, アラインメント] [: formatString]} です。 'index' を指定する書式設定対象オブジェクトの 0 から始まる整数です。 オブジェクトには、書式文字列に対応するインデックスがない、オブジェクトは無視されます。 'Index' で指定されたオブジェクトが存在しない場合、<xref:System.FormatException?displayProperty=fullName>が実行時にスローされます。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、各オブジェクトの引数の書式項目を指定および各書式項目のオブジェクトの引数を提供します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 次の例では、ルールの 2 つの違反を示します。  
  
 [!code-vb[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/VisualBasic/ca2241-provide-correct-arguments-to-formatting-methods_1.vb)]
 [!code-csharp[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/CSharp/ca2241-provide-correct-arguments-to-formatting-methods_1.cs)]