---
title: CA2112:セキュリティで保護された型はフィールドを公開してはなりません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d4786b51536d9df7c51c8551b5fbd8d863879875
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53920405"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112:セキュリティで保護された型はフィールドを公開してはなりません

|||
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたはプロテクト型はパブリック フィールドを格納し、によってセキュリティ保護されて、[リンク確認要求](/dotnet/framework/misc/link-demands)します。

## <a name="rule-description"></a>規則の説明
 リンク確認要求で保護されている型のインスタンスに対するアクセス権がコードにある場合、その型のフィールドにアクセスするためにリンク確認要求に適合する必要はありません。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するのには、非パブリック フィールドを作成し、パブリック プロパティまたはフィールド データを返すメソッドを追加します。 Linkdemand 型では、型のプロパティおよびメソッドへのアクセスを保護します。 ただし、コード アクセス セキュリティは、フィールドには適用されません。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 両方のセキュリティの問題と適切なデザイン、パブリック フィールドの非パブリックのことで違反を修正する必要があります。 このルールから警告を抑制するには、フィールドはセキュリティで保護された、必要のある情報を保持しない場合と、フィールドの内容に依存しない場合。

## <a name="example"></a>例
 次の例は、ライブラリの種類で構成されます (`SecuredTypeWithFields`) 型、セキュリティ保護されていないフィールドを持つ (`Distributor`) インスタンス型には、それらを作成するアクセス許可はなく、アプリケーションのコードをライブラリの種類のインスタンスを作成することができます種類をセキュリティで保護するアクセス許可があるない場合でも、インスタンスのフィールドを読み取ることができます。

 次のライブラリ コードでは、この規則に違反します。

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]

## <a name="example-1"></a>例 1
 アプリケーションでは、リンク確認要求、セキュリティで保護された型を保護するため、インスタンスを作成できません。 次のクラスは、セキュリティで保護された型のインスタンスを取得するアプリケーションを使用できます。

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]

## <a name="example-2"></a>例 2
 次のアプリケーションは、方法、セキュリティで保護された型のメソッドへのアクセスの許可なくコード フィールドにアクセスできるかを示しています。

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_3.cs)]

この例を実行すると、次の出力が生成されます。

```txt
Creating an instance of SecuredTypeWithFields.
Secured type fields: 22, 33
Changing secured type's field...
Cached Object fields: 99, 33
```

## <a name="related-rules"></a>関連するルール

- [CA 1051:インスタンス フィールドを宣言しません](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>関連項目

- [リンク確認要求](/dotnet/framework/misc/link-demands)
- [データとモデリング](/dotnet/framework/data/index)