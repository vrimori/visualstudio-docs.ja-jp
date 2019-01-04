---
title: CA2237:ISerializable 型を SerializableAttribute に設定します
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8918b00ff7138c1e59644a0d124c3c3f9487ad4a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838808"
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237:ISerializable 型を SerializableAttribute に設定します

|||
|-|-|
|TypeName|MarkISerializableTypesWithSerializable|
|CheckId|CA2237|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 外部から参照の型を実装して、<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>インターフェイスと、型がでマークされていない、<xref:System.SerializableAttribute?displayProperty=fullName>属性。 ルールは、派生型が基本型をシリアル化できませんを無視します。

## <a name="rule-description"></a>規則の説明
 シリアル化可能として共通言語ランタイムによって認識される型をマークする必要があります、<xref:System.SerializableAttribute>属性の型の実装を通じてカスタムのシリアル化ルーチンを使用する場合でも、<xref:System.Runtime.Serialization.ISerializable>インターフェイス。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、適用、<xref:System.SerializableAttribute>属性を型にします。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 アプリケーション ドメイン間で正常にシリアル化する必要があるため、この規則の例外クラスからの警告を抑制しないでください。

## <a name="example"></a>例
 次の例では、規則に違反する型を示します。 コメントを解除、<xref:System.SerializableAttribute>規則に適合する行の属性します。

 [!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
 [!code-csharp[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]

## <a name="related-rules"></a>関連するルール
 [CA 2236:ISerializable 型の基本クラス メソッドを呼び出す](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240:ISerializable を正しく実装します。](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: シリアル化コンストラクターを実装します](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA 2238:シリアル化メソッドを正しく実装します。](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235:すべてのシリアル化不可能なフィールドをマークします。](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2239:オプションのフィールドに逆シリアル化メソッドを提供します。](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120:セキュリティで保護されたシリアル化コンス トラクター](../code-quality/ca2120-secure-serialization-constructors.md)