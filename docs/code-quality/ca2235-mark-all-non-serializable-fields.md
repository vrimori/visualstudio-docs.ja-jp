---
title: CA2235:すべてのシリアル化不可能なフィールドを設定します
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 40a4326924d83d4604f512f41f85e7adb8d21bb6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54975050"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235:すべてのシリアル化不可能なフィールドを設定します

|||
|-|-|
|TypeName|MarkAllNonSerializableFields|
|CheckId|CA2235|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 シリアル化できない型のインスタンス フィールドが、シリアル化できる型で宣言されています。

## <a name="rule-description"></a>規則の説明
 シリアル化可能な型は、いずれかでマークされている、<xref:System.SerializableAttribute?displayProperty=fullName>属性。 型がシリアル化されるとき、<xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName>型にシリアル化可能でない型のインスタンス フィールドが含まれている場合、例外がスローされます。

 この例外は、型を使用してカスタムのシリアル化を使用して、<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>インターフェイス。 このインターフェイスを実装する型が、独自のシリアル化ロジックを提供し、このような型のシリアル化不可能なインスタンス フィールドで CA2235 は適用されませんのでします。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、適用、<xref:System.NonSerializedAttribute?displayProperty=fullName>属性をシリアル化可能でないフィールド。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 場合にこの規則による警告を抑制するのみ、<xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName>シリアル化および逆シリアル化するフィールドのインスタンスを利用できる型を宣言します。

## <a name="example"></a>例
 次の例では、規則に違反する型と、規則に適合する型を示します。

 [!code-csharp[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]

## <a name="related-rules"></a>関連するルール
 [CA2236:ISerializable 型の基本クラス メソッドを呼び出す](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240:ISerializable を正しく実装します。](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: シリアル化コンストラクターを実装します](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238:シリアル化メソッドを正しく実装します。](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2237:ISerializable 型を serializableattribute に設定します](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239:オプションのフィールドに逆シリアル化メソッドを提供します。](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120:セキュリティで保護されたシリアル化コンス トラクター](../code-quality/ca2120-secure-serialization-constructors.md)
