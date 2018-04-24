---
title: 'Ca 2101: が P 呼び出し文字列引数に対してマーシャ リングを指定します'
ms.date: 11/04/2016
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
ms.openlocfilehash: 8171c318d419edc49410c44d381e82f088014082
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101: P/Invoke 文字列引数に対してマーシャリングを指定します
|||
|-|-|
|TypeName|SpecifyMarshalingForPInvokeStringArguments|
|CheckId|CA2101|
|カテゴリ|Microsoft.Globalization|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 プラットフォーム呼び出しメンバー部分的に信頼された呼び出し元の文字列パラメーターを持つことができ、文字列が明示的にマーシャ リングできません。

## <a name="rule-description"></a>規則の説明
 Unicode から ANSI に変換するときは、特定の ANSI コード ページですべての Unicode 文字を表現できることが可能です。 *最適マッピング*の文字を表現できない文字に置き換えることによってこの問題を解決しようとしています。 この機能の使用可能性選択される文字は制御できないので、潜在的なセキュリティの脆弱性があります。 たとえば、悪意のあるコードに意図的に作成など、ファイル システムの特殊文字に変換されますが、特定のコード ページに記載されていない文字を含む Unicode 文字列 '.. ' または '/' です。 特殊文字のセキュリティ チェックは、文字列は ANSI に変換する前に頻繁に発生することにも注意してください。

 最適マッピングは、アンマネージの変換では、バイトを WChar の既定値です。 最適マッピングを明示的に無効にする場合を除き、コードは、この問題のため、利用可能なセキュリティの脆弱性を含むもあります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、文字列データ型を明示的にマーシャ リングします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、この規則に違反し、違反の修正方法を表示するメソッドを示します。

 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]