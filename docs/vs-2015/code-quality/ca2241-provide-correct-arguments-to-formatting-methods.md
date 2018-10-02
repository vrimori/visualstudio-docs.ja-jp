---
title: ': Ca 2241 正しい引数を書式設定メソッド |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6d3b190adfb67e90a50da80453d8ce2db5013723
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47592383"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: 正しい引数を書式指定メソッドに指定します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CA2241: 正しい引数を書式設定メソッドを提供](https://docs.microsoft.com/visualstudio/code-quality/ca2241-provide-correct-arguments-to-formatting-methods)します。

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

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、ルールの 2 つの違反を示します。

 [!code-csharp[FxCop.Usage.FormattingArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/cs/FxCop.Usage.FormattingArguments.cs#1)]
 [!code-vb[FxCop.Usage.FormattingArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/vb/FxCop.Usage.FormattingArguments.vb#1)]



