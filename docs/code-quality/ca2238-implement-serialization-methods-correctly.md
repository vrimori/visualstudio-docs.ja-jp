---
title: CA2238:シリアル化メソッドを正しく実装します
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
helpviewer_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
ms.assetid: 00882cf9-e10d-4d40-9126-3e6753e3c934
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: fb1c8198bb9aeda12fe773ca7b9c5f00321d691d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996572"
---
# <a name="ca2238-implement-serialization-methods-correctly"></a>CA2238:シリアル化メソッドを正しく実装します

|||
|-|-|
|TypeName|ImplementSerializationMethodsCorrectly|
|CheckId|CA2238|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|– メソッドは、アセンブリ外部から参照できる場合。<br /><br /> なし - メソッドが、アセンブリの外部に表示されない場合|

## <a name="cause"></a>原因
 シリアル化イベントを処理するメソッドに、適切なシグネチャ、戻り値の型、または参照範囲がありません。

## <a name="rule-description"></a>規則の説明
 メソッドは、シリアル化イベントのハンドラーをシリアル化イベントの次の属性のいずれかの操作を適用することによって指定されます。

- <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>

  シリアル化イベントのハンドラーが型の 1 つのパラメーターを受け取る<xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>、return `void`、いて`private`可視性。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、シグネチャ、戻り値の型、またはシリアル化のイベント ハンドラーの可視性を修正します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例は、イベント ハンドラーを正しく宣言されているシリアル化に示します。

 [!code-vb[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/VisualBasic/ca2238-implement-serialization-methods-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/CSharp/ca2238-implement-serialization-methods-correctly_1.cs)]

## <a name="related-rules"></a>関連するルール
 [CA2236:ISerializable 型の基本クラス メソッドを呼び出す](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240:ISerializable を正しく実装します。](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: シリアル化コンストラクターを実装します](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2235:すべてのシリアル化不可能なフィールドをマークします。](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237:ISerializable 型を serializableattribute に設定します](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239:オプションのフィールドに逆シリアル化メソッドを提供します。](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120:セキュリティで保護されたシリアル化コンス トラクター](../code-quality/ca2120-secure-serialization-constructors.md)