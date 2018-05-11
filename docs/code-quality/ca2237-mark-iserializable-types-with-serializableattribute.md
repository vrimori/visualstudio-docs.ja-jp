---
title: 'CA2237: ISerializable 型を SerializableAttribute に設定します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4b7efc13eaee32662688593ff0cb94d9c0cb7a8a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237: ISerializable 型を SerializableAttribute に設定します
|||
|-|-|
|TypeName|MarkISerializableTypesWithSerializable|
|CheckId|CA2237|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 外部から参照できる型が実装する、<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>インターフェイスと、型がでマークされていない、<xref:System.SerializableAttribute?displayProperty=fullName>属性。 ルールは、派生型の基本型はシリアル化できませんを無視します。

## <a name="rule-description"></a>規則の説明
 シリアル化可能として共通言語ランタイムによって認識される型をマークする必要があります、<xref:System.SerializableAttribute>属性の型の実装を通じてカスタムのシリアル化ルーチンを使用する場合でも、<xref:System.Runtime.Serialization.ISerializable>インターフェイスです。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、適用、<xref:System.SerializableAttribute>属性を型にします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 アプリケーション ドメイン間で正しく動作するシリアル化できる必要があるために、例外クラスにはこの規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例は、規則に違反する型を示しています。 コメントを解除、<xref:System.SerializableAttribute>規則に適合する行の属性です。

 [!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
 [!code-csharp[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]

## <a name="related-rules"></a>関連規則
 [CA2236: ISerializable 型で基本クラス メソッドを呼び出します](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: ISerializable を正しく実装します](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: シリアル化コンストラクターを実装します](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: シリアル化メソッドを正しく実装します](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: すべてのシリアル化不可能なフィールドを設定します](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2239: オプションのフィールドに逆シリアル化メソッドを指定します](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: シリアル化コンストラクターをセキュリティで保護します](../code-quality/ca2120-secure-serialization-constructors.md)