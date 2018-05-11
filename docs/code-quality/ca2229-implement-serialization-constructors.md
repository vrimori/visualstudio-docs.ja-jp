---
title: 'CA2229: シリアル化コンストラクターを実装します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 72a27fefd0fa64e3218ccb6578f7dabb94ea4ae6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229: シリアル化コンストラクターを実装します
|||
|-|-|
|TypeName|ImplementSerializationConstructors|
|CheckId|CA2229|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 型が実装、<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>インターフェイス、インターフェイス、またはデリゲートではないと、次の条件のいずれかが当てはまる。

-   型が使用するコンス トラクターを持たない、<xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>オブジェクトおよび<xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>オブジェクト (シリアル化コンス トラクターのシグネチャ)。

-   型が封印されていないと、シリアル化コンス トラクターのアクセス修飾子は保護された (ファミリー) ではありません。

-   型がシールされている、シリアル化コンス トラクターのアクセス修飾子がプライベートではありません。

## <a name="rule-description"></a>規則の説明
 このルールは、カスタムのシリアル化をサポートする型に関係します。 型は、実装している場合、カスタムのシリアル化をサポートしている、<xref:System.Runtime.Serialization.ISerializable>インターフェイスです。 シリアル化コンス トラクターは、逆シリアル化、またはを使用してシリアル化されたオブジェクトを再作成に必要な<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>メソッドです。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、シリアル化コンストラクターを実装します。 シールされたクラスの場合、コンストラクターをプライベートにするか、プロテクトにします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 規則の違反は抑制しないでください。 型は、逆シリアル化されませんされ、多くのシナリオでは機能しません。

## <a name="example"></a>例
 次の例は、規則に適合する型を示しています。

 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]

## <a name="related-rules"></a>関連規則
 [CA2237: ISerializable 型を SerializableAttribute に設定します](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>関連項目
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>