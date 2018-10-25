---
title: 'CA2101: P/Invoke 文字列引数に対してマーシャリングを指定します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 21b3ab30ff6672149fe05359f33ad932706a8a91
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867313"
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101: P/Invoke 文字列引数に対してマーシャリングを指定します

|||
|-|-|
|TypeName|SpecifyMarshalingForPInvokeStringArguments|
|CheckId|CA2101|
|カテゴリ|Microsoft.Globalization|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 プラットフォーム呼び出しメンバーにより部分的に信頼された呼び出し元は、文字列パラメーターを持つし、文字列が明示的にマーシャ リングされません。

## <a name="rule-description"></a>規則の説明
 Unicode から ANSI に変換することが特定の ANSI コード ページですべての Unicode 文字を表現できることができます。 *最適マッピング*の文字を表現できない文字に置き換えることによってこの問題を解決しようとしています。 選択されている文字は制御できないため、この機能の使用にはセキュリティの脆弱性を潜在的な可能性があります。 たとえば、悪意のあるコードをなど、ファイル システムの特殊文字に変換されます、特定のコード ページではない文字を含む Unicode 文字列に意図的に作成 '… ' または '/'。 特殊文字のセキュリティ チェックは、文字列が ANSI に変換される前に頻繁に発生することにも注意してください。

 最適マッピングでは、非管理対象の変換では、バイトを WChar の既定値です。 最適マッピングを明示的に無効にした場合を除き、コードはこの問題のため、悪用可能なセキュリティの脆弱性を含む可能性があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、文字列データ型を明示的にマーシャ リングします。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、この規則に違反し、違反を修正する方法を示しますメソッドを示します。

 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]