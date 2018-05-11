---
title: 'CA2240: ISerializable を正しく実装します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bfd13bb09e8e9e3338ed37723f74ca42b09fdeb3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: ISerializable を正しく実装します
|||
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 外部から参照できる型が、<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>インターフェイスと、次の条件のいずれかが true:

-   型が継承しますが、オーバーライドしません、<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>メソッドと型の宣言でマークされていないインスタンス フィールド、<xref:System.NonSerializedAttribute?displayProperty=fullName>属性。

-   型は封印されていないと、型が実装する、<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>しないメソッドが外部から可視性およびオーバーライド可能です。

## <a name="rule-description"></a>規則の説明
 インスタンス フィールドを継承する型で宣言されている、<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>インターフェイスは、自動的にシリアル化プロセスには含まれません。 フィールドを含めるには、型を実装する必要があります、<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>メソッドと、シリアル化コンス トラクターです。 フィールドはシリアル化する必要がありますいない場合は、適用、<xref:System.NonSerializedAttribute>属性は、意思決定を明示的に示すフィールドにします。

 シールされていないの実装の種類で、<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>メソッドを外部から参照可能にする必要があります。 そのため、このメソッドは派生型から呼び出すことができ、オーバーライドできます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するように、<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>メソッドが表示され、オーバーライド可能なすべてのインスタンス フィールドのシリアル化プロセスに含まれるまたはで明示的にマークされていることを確認し、<xref:System.NonSerializedAttribute>属性。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、規則に違反する次の 2 つのシリアル化できる型を示します。

 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]

## <a name="example"></a>例
 次の例では、2 つの以前の違反を修正の上書き可能な実装を提供することによって<xref:System.Runtime.Serialization.ISerializable.GetObjectData>の実装を提供して Book クラスに`GetObjectData`ライブラリ クラスです。

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]

## <a name="related-rules"></a>関連規則
 [Ca 2236: ISerializable 型で基底クラス メソッドの呼び出し](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md) [ca 2229: シリアル化コンス トラクターを実装する](../code-quality/ca2229-implement-serialization-constructors.md) [ca 2238: シリアル化メソッドを正しく実装](../code-quality/ca2238-implement-serialization-methods-correctly.md) [: Ca 2235 すべてのシリアル化できないフィールド](../code-quality/ca2235-mark-all-non-serializable-fields.md) [ca 2237: ISerializable 型を SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md) [ca 2239: 提供省略可能なフィールドメソッドの逆シリアル化](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md) [CA2120: シリアル化コンス トラクターをセキュリティで保護](../code-quality/ca2120-secure-serialization-constructors.md)
