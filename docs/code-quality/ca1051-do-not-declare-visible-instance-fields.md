---
title: 'CA1051: 参照できるインスタンス フィールドを宣言しないでください'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc08d39e842afa8bee9baa89f4c788f291d90ea2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: 参照できるインスタンス フィールドを宣言しないでください
|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 外部から参照できる型では、外部から参照できるインスタンス フィールドを持ちます。

## <a name="rule-description"></a>規則の説明
 フィールドの主な用途は、実装の詳細にする必要があります。 フィールドでなければなりません`private`または`internal`し、プロパティを使用して公開する必要があります。 プロパティにアクセスすると、フィールドにアクセスする方が重大な変更を導入することがなく展開し、型の機能とプロパティのアクセサーでコードを変更できますに簡単です。 プライベートまたは内部フィールドの値を返すプロパティが; フィールドへのアクセスに従ったを実行する最適化されました。ほとんどのパフォーマンス向上は、プロパティを外部から参照できるフィールドの使用に関連付けられません。

 外部から参照`public`、 `protected`、および`protected internal`(`Public`、 `Protected`、および`Protected Friend`Visual Basic で) アクセシビリティ レベル。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するため、フィールド`private`または`internal`および外部から参照できるプロパティを使用して公開します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 外部から参照できるフィールドは、プロパティに提供される利点を提供しません。 さらに、パブリック フィールドで保護することはできません[リンク確認要求](/dotnet/framework/misc/link-demands)です。 参照してください[ca 2112: セキュリティで保護された型はフィールドを公開する必要があります](../code-quality/ca2112-secured-types-should-not-expose-fields.md)です。

## <a name="example"></a>例
 次の例は、型を示しています (`BadPublicInstanceFields`) この規則に違反します。 `GoodPublicInstanceFields` 修正後のコードを示します。

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]

## <a name="related-rules"></a>関連規則
 [CA2112: セキュリティで保護された型はフィールドを公開してはなりません](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>関連項目
 [リンク確認要求](/dotnet/framework/misc/link-demands)