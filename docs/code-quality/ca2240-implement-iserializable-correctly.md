---
title: CA2240:ISerializable を正しく実装します
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1924b86945df73ccd84f1215367d44d9ead039aa
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54971287"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240:ISerializable を正しく実装します

|||
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因

割り当てることは、外部から参照できる型は、<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>インターフェイスと、次の条件のいずれかが true:

- 型の継承がオーバーライドしません、<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>メソッドと型の宣言でマークされていないインスタンス フィールド、<xref:System.NonSerializedAttribute?displayProperty=fullName>属性。

- 型がシールされていないと、型を実装、<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>が外部で表示され、オーバーライド可能なメソッドです。

## <a name="rule-description"></a>規則の説明
 インスタンス フィールドを継承する型で宣言されている、<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>インターフェイスは、自動的にシリアル化プロセスには含まれません。 フィールドは、型を実装する必要があります、<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>メソッドとシリアル化コンス トラクター。 フィールドをシリアル化する必要がありますしない場合は、適用、<xref:System.NonSerializedAttribute>意思決定を明示的に示すフィールドに属性します。

 シールされていない、実装の種類で、<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>メソッドを外部から参照可能にする必要があります。 そのため、メソッドは、派生型は、呼び出すことができ、オーバーライド可能なは。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するように、<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>メソッドをオーバーライドできるすべてのインスタンス フィールドをシリアル化プロセスに含まれるかで明示的にマークされていることを確認して、<xref:System.NonSerializedAttribute>属性。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、ルールに違反している 2 つのシリアル化可能な型を示します。

 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]

## <a name="example"></a>例
 次の例では、前の 2 つの違反を修正の上書き可能な実装を提供して<xref:System.Runtime.Serialization.ISerializable.GetObjectData>Book クラスの実装を提供すること、および`GetObjectData`ライブラリ クラス。

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]

## <a name="related-rules"></a>関連するルール

- [CA2236:ISerializable 型の基本クラス メソッドを呼び出す](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2229: シリアル化コンストラクターを実装します](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2238:シリアル化メソッドを正しく実装します。](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2235:すべてのシリアル化不可能なフィールドをマークします。](../code-quality/ca2235-mark-all-non-serializable-fields.md)
- [CA2237:ISerializable 型を serializableattribute に設定します](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2239:オプションのフィールドに逆シリアル化メソッドを提供します。](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2120:セキュリティで保護されたシリアル化コンス トラクター](../code-quality/ca2120-secure-serialization-constructors.md)