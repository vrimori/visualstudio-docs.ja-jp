---
title: 'CA2236: ISerializable 型で基本クラス メソッドを呼び出します'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b7bc90dfd0cf786bbd4e2494a6c65e2c19ff4eb6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236: ISerializable 型で基本クラス メソッドを呼び出します
|||
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 型を実装する型から派生して、<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>インターフェイス、および、次の条件のいずれかが true:

-   型がシリアル化コンス トラクターを持つコンス トラクターを実装、 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>、<xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>パラメーター シグネチャが、基本型のシリアル化コンス トラクターを呼び出しません。

-   型が実装、<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>メソッドは呼び出しませんが、<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>基本型のメソッドです。

## <a name="rule-description"></a>規則の説明
 型が実装するカスタムのシリアル化のプロセスで、<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>フィールドがあり、フィールドを逆シリアル化のシリアル化コンス トラクターをシリアル化するメソッド。 型を実装する型から派生している場合、<xref:System.Runtime.Serialization.ISerializable>インターフェイス、基本型<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>メソッドとシリアル化コンス トラクター呼び出す必要がありますにシリアル化/非 serialize 基本型のフィールドです。 それ以外の場合、型がないシリアル化および正しく逆シリアル化します。 派生型が、新しいフィールドを追加しない場合、型が必要がないことを実装するに注意してください、<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>メソッドもシリアル化コンス トラクターまたは同等の基本型を呼び出します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、基本型を呼び出す<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>から、対応するメソッドまたはシリアル化コンス トラクターは派生型のメソッドまたはコンス トラクターです。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、シリアル化コンス トラクターを呼び出すことによって、規則に適合する派生型および<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>基底クラスのメソッドです。

 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)]
 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]

## <a name="related-rules"></a>関連規則
 [CA2240: ISerializable を正しく実装します](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: シリアル化コンストラクターを実装します](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: シリアル化メソッドを正しく実装します](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: すべてのシリアル化不可能なフィールドを設定します](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: ISerializable 型を SerializableAttribute に設定します](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: オプションのフィールドに逆シリアル化メソッドを指定します](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: シリアル化コンストラクターをセキュリティで保護します](../code-quality/ca2120-secure-serialization-constructors.md)