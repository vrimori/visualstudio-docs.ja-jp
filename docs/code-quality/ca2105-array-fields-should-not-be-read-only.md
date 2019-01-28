---
title: CA2105:配列フィールドを読み取り専用にすることはできません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4bfa7127a645ea2d53a85784297d8da43ee59038
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54939232"
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105:配列フィールドを読み取り専用にすることはできません

|||
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|CheckId|CA2105|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因

読み取り専用配列を保持するパブリックまたはプロテクト フィールドが宣言されています。

## <a name="rule-description"></a>規則の説明

適用すると、 `readonly` (`ReadOnly`で[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 修飾子を配列フィールドを含むフィールドを変更して、別の配列を参照してくださいことはできません。 ただし、読み取り専用フィールドに格納された配列の要素は変更できます。 判断したり、パブリックにアクセスできる読み取り専用配列の要素に基づく操作を実行するコードには、悪用可能なセキュリティの脆弱性が含まれます。

メモをパブリック フィールドを持つデザイン規則に違反しても[ca 1051。インスタンス フィールドを宣言しない](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)します。

## <a name="how-to-fix-violations"></a>違反の修正方法

このルールで識別されるセキュリティの脆弱性を修正するのに依存しないパブリックにアクセスできる読み取り専用配列の内容。 次の手順のいずれかを使用することを強くお勧めします。

- 厳密に型指定されたコレクションは変更できない配列に置き換えます。 詳細については、「 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName> 」を参照してください。

- プライベート配列の複製を返すメソッドでは、パブリック フィールドを置き換えます。 コードが、複製に依存しないためにありません危険要素が変更された場合です。

2 番目の方法を選択した場合、フィールドと置き換えないでプロパティ悪影響を与える、配列を返すプロパティは、パフォーマンスに影響します。 詳細については、次を参照してください。 [ca 1819。プロパティは、配列を返す必要がありますいない](../code-quality/ca1819-properties-should-not-return-arrays.md)します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

この規則による警告の除外はお勧めします。 読み取り専用フィールドの内容が重要ではない場合はほとんどありませんが発生します。 シナリオの場合は場合、削除、`readonly`修飾子の代わりに、メッセージを除外します。

## <a name="example-1"></a>例 1

この例では、この規則に違反する危険性を示します。 最初の部分は、型を持つサンプル ライブラリを示しています。 `MyClassWithReadOnlyArrayField`、2 つのフィールドを格納している (`grades`と`privateGrades`) を安全ではありません。 フィールド`grades`はパブリックであり、そのため、呼び出し元に対して脆弱になります。 フィールド`privateGrades`はプライベートであるが、呼び出し元に返されるため、脆弱なままです、`GetPrivateGrades`メソッド。 `securePrivateGrades`フィールドが、安全な方法で公開されている、`GetSecurePrivateGrades`メソッド。 優れた設計のプラクティスに従うにはプライベートとして宣言されています。 2 番目の部分に格納された値を変更するコードを示しています、`grades`と`privateGrades`メンバー。

サンプルのクラス ライブラリは、次の例が表示されます。

[!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_1.cs)]

## <a name="example-2"></a>例 2

次のコードでは、読み取り専用配列セキュリティの問題を説明するために、例のクラス ライブラリを使用します。

[!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_2.cs)]

この例の出力は次のとおりです。

```text
Before tampering: Grades: 90, 90, 90 Private Grades: 90, 90, 90  Secure Grades, 90, 90, 90
After tampering: Grades: 90, 555, 90 Private Grades: 90, 555, 90  Secure Grades, 90, 90, 90
```

## <a name="see-also"></a>関連項目

- <xref:System.Array?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>