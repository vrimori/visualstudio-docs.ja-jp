---
title: CA2229:シリアル化コンストラクターを実装します
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 2228f25c344e7471c0ee8ff252d88a5454345999
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53840305"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229:シリアル化コンストラクターを実装します

|||
|-|-|
|TypeName|ImplementSerializationConstructors|
|CheckId|CA2229|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 型が実装、<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>インターフェイス、デリゲートまたはインターフェイスではないと、次の条件のいずれかが true:

- 型には、取得するコンス トラクターはありません、<xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>オブジェクトと<xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>オブジェクト (シリアル化コンス トラクターの署名)。

- 型が封印されていないと、そのシリアル化コンス トラクターのアクセス修飾子が保護された (ファミリ) ではありません。

- 型がシールされている、シリアル化コンス トラクターのアクセス修飾子がプライベートではありません。

## <a name="rule-description"></a>規則の説明
 このルールは、カスタムのシリアル化をサポートする型に関連します。 型は、実装している場合、カスタムのシリアル化をサポートしている、<xref:System.Runtime.Serialization.ISerializable>インターフェイス。 シリアル化コンス トラクターは、逆シリアル化、またはを使用してシリアル化されたオブジェクトを再作成に必要な<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>メソッド。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、シリアル化コンストラクターを実装します。 シールされたクラスの場合、コンストラクターをプライベートにするか、プロテクトにします。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 ルールの違反を抑制しないでください。 型を使用して、逆シリアル化はならず、多くのシナリオでは機能しません。

## <a name="example"></a>例
 次の例では、規則に適合する型を示します。

 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]

## <a name="related-rules"></a>関連するルール
 [CA 2237:ISerializable 型を serializableattribute に設定します](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>関連項目

- <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>
- <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
- <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>