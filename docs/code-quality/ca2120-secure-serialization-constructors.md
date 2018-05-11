---
title: 'CA2120: シリアル化コンストラクターをセキュリティで保護します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2120
- SecureSerializationConstructors
helpviewer_keywords:
- SecureSerializationConstructors
- CA2120
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 449258d04b6a47fef42c56637a4de48a4e5d1d12
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120: シリアル化コンストラクターをセキュリティで保護します
|||
|-|-|
|TypeName|SecureSerializationConstructors|
|CheckId|CA2120|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 型が実装、<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>インターフェイス インターフェイス、またはデリゲートではないと、部分的に信頼された呼び出し元を許可するアセンブリで宣言されています。 型を受け取るコンス トラクターがある、<xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>オブジェクトおよび<xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>オブジェクト (シリアル化コンス トラクターのシグネチャ)。 このコンス トラクターは、セキュリティ チェックによって保護されませんが、型の通常のコンス トラクターの 1 つ以上のセキュリティで保護されます。

## <a name="rule-description"></a>規則の説明
 このルールは、カスタムのシリアル化をサポートする型に関係します。 型は、実装している場合、カスタムのシリアル化をサポートしている、<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>インターフェイスです。 シリアル化コンス トラクターが必要と逆シリアル化、またはを使用してシリアル化されたオブジェクトを再作成に使用される、<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>メソッドです。 シリアル化コンス トラクターは、オブジェクトの初期化、ためセキュリティ チェックの標準コンス トラクターに組み込まれている必要がありますにも存在するシリアル化コンス トラクターです。 この規則に違反する場合、インスタンスがそれ以外の場合に作成できませんでしたの呼び出し元は、これを行うにシリアル化コンス トラクターを使用できます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、他のコンス トラクターを保護するものと同じであるセキュリティ確認要求でシリアル化コンス トラクターを保護します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 規則の違反は抑制しないでください。

## <a name="example"></a>例
 次の例は、規則に違反する型を示しています。

 [!code-csharp[FxCop.Security.SerialCtors#1](../code-quality/codesnippet/CSharp/ca2120-secure-serialization-constructors_1.cs)]

## <a name="related-rules"></a>関連規則
 [CA2229: シリアル化コンストラクターを実装します](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2237: ISerializable 型を SerializableAttribute に設定します](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>関連項目
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>