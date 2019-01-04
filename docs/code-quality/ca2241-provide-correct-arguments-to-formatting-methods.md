---
title: CA2241:書式設定メソッドに正しい引数を提供
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
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
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: df71a51336f559f293faad86c161b9939a3a8014
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53912978"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241:書式設定メソッドに正しい引数を提供

|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 `format`などのメソッドに渡される引数を文字列<xref:System.Console.WriteLine%2A>、 <xref:System.Console.Write%2A>、または<xref:System.String.Format%2A?displayProperty=fullName>に各オブジェクトの引数、またはその逆に対応する書式指定項目が含まれていません。

## <a name="rule-description"></a>規則の説明
 などのメソッドに引数<xref:System.Console.WriteLine%2A>、 <xref:System.Console.Write%2A>、および<xref:System.String.Format%2A>続くいくつかの書式指定文字列から成る<xref:System.Object?displayProperty=fullName>インスタンス。 テキストと、フォームの埋め込みの書式項目の書式指定文字列で構成されます {インデックス [, の配置] [: formatString]} です。 'インデックス' は、書式設定するオブジェクトの中を示す 0 から始まる整数です。 オブジェクトには、書式指定文字列に対応するインデックスがない、オブジェクトは無視されます。 'インデックス' で指定したオブジェクトが存在しない場合、<xref:System.FormatException?displayProperty=fullName>が実行時にスローされます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則の違反を修正するには、書式指定項目は、各オブジェクトの引数と各書式項目のオブジェクトの引数を提供します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、ルールの 2 つの違反を示します。

 [!code-vb[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/VisualBasic/ca2241-provide-correct-arguments-to-formatting-methods_1.vb)]
 [!code-csharp[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/CSharp/ca2241-provide-correct-arguments-to-formatting-methods_1.cs)]