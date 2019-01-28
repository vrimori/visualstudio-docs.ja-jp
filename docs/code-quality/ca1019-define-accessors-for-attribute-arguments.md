---
title: CA1019:属性引数にアクセサーを定義します
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8a604ea8731108c73c3dfb1c279f2f243c0a05ad
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54931181"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019:属性引数にアクセサーを定義します

|||
|-|-|
|TypeName|DefineAccessorsForAttributeArguments|
|CheckId|CA1019|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 そのコンス トラクターでは、属性は、対応するプロパティがない引数を定義します。

## <a name="rule-description"></a>規則の説明
 属性では、対象に適用するときに必ず指定する必須の引数を定義できます。 この引数は、コンストラクターに位置指定パラメーターで属性を指定できるようになるため、位置指定引数とも呼ばれます。 必須のすべての引数について、対応する読み取り専用のプロパティも属性で規定する必要があります。これは、引数値を実行時に取得できるようにするためです。 このルールは、各コンス トラクターのパラメーターの対応するプロパティを定義したかを確認します。

 また、属性ではオプションの引数も定義できます。これは名前付き引数とも呼ばれます。 この引数は、名前でコンストラクターに属性を指定するときに使用されます。また、対応する読み取り/書き込みプロパティが必要です。

 必須およびオプションの引数では、対応するプロパティとコンス トラクターのパラメーターを使用する必要があります、同じ名前が異なる大文字小文字の区別を付けます。 プロパティは pascal 形式を使用する大文字と小文字、およびパラメーター使用して camel 規約に従った大文字小文字の区別します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、コンス トラクターのパラメーターがない 1 つの読み取り専用プロパティを追加します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 取得できる必須の引数の値したくない場合は、この規則による警告を抑制します。

## <a name="custom-attributes-example"></a>カスタム属性の例

次の例では、必須 (位置) パラメーターを定義する 2 つの属性を示します。 属性の最初の実装が正しく定義されていません。 2 番目の実装が正しいです。

[!code-csharp[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_1.cs)]
[!code-vb[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/VisualBasic/ca1019-define-accessors-for-attribute-arguments_1.vb)]

## <a name="positional-and-named-arguments"></a>位置指定引数と名前付き引数

位置指定引数と名前付き引数は、どの引数には、属性の必須とする引数は省略可能なライブラリのコンシューマーのチェック ボックスをオフになります。

次の例は、位置指定引数と名前付きの両方の引数を持つ属性の実装を示しています。

[!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_2.cs)]

次の例では、2 つのプロパティをカスタム属性を適用する方法を示します。

[!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_3.cs)]

## <a name="related-rules"></a>関連するルール
 [CA1813:シールされていない属性します。](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>関連項目
 [属性](/dotnet/standard/design-guidelines/attributes)