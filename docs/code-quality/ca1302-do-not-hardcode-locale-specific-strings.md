---
title: CA1302:ロケール特有の文字列をハードコードしません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b05f1aa31a38ff4f8e707d53d062abe3d10617fd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53827729"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302:ロケール特有の文字列をハードコードしません

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|カテゴリ|Microsoft.Globalization|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 メソッドは、特定のシステム フォルダーのパスの部分を表す文字列リテラルを使用します。

## <a name="rule-description"></a>規則の説明
 <xref:System.Environment.SpecialFolder?displayProperty=fullName>列挙が特殊なシステム フォルダーを参照するメンバーが含まれます。 これらのフォルダーの場所は、さまざまなオペレーティング システムで異なる値を持つことができます、ユーザーは、いくつかの場所を変更できるし、位置がローカライズされます。 特別なフォルダーの例の"C:\WINDOWS\system32"は、[システム] フォルダーは、[!INCLUDE[winxp](../code-quality/includes/winxp_md.md)]が上には、"C:\WINNT\system32"[!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)]します。 <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName>メソッドが関連付けられている場所を返します、<xref:System.Environment.SpecialFolder>列挙体。 によって返される場所<xref:System.Environment.GetFolderPath%2A>はローカライズされ、現在実行中のコンピューターに適切な。

 このルールを使用して取得されるフォルダーのパスをトークン化、<xref:System.Environment.GetFolderPath%2A>メソッドの別のディレクトリのレベルにします。 各文字列リテラルは、トークンと比較されます。 一致が見つかった場合、メソッドがトークンに関連付けられているシステムの場所を表す文字列を構築するいると見なされます。 移植性と、使用、<xref:System.Environment.GetFolderPath%2A>文字列リテラルを使用する代わりに特殊なシステム フォルダーの場所を取得するメソッド。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するを使用して場所を取得、<xref:System.Environment.GetFolderPath%2A>メソッド。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 関連付けられているシステムの場所のいずれかを参照する文字列リテラルを使用しない場合は、この規則による警告を抑制するのには安全では、<xref:System.Environment.SpecialFolder>列挙体。

## <a name="example"></a>例
 次の例では、この規則から 3 つの警告を生成します。 一般的なアプリケーション データ フォルダーのパスを構築します。 次に、例を使用して、パスを取得、<xref:System.Environment.GetFolderPath%2A>メソッド。

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]

## <a name="related-rules"></a>関連するルール
 [CA 1303:ローカライズされたパラメーターとしてリテラルを渡さないでください。](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)