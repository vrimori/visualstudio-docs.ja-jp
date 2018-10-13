---
title: 'CA2120: シリアル化コンス トラクターをセキュリティ保護 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2120
- SecureSerializationConstructors
helpviewer_keywords:
- SecureSerializationConstructors
- CA2120
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 02f06a4636aa653b4dc790f40ac64ab907c534e5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49300795"
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120: シリアル化コンストラクターをセキュリティで保護します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|SecureSerializationConstructors|
|CheckId|CA2120|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 型が実装、<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>インターフェイス、デリゲートまたはインターフェイスではないと、部分的に信頼された呼び出し元を許可するアセンブリで宣言されています。 型を受け取るコンス トラクターがある、<xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>オブジェクトと<xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>オブジェクト (シリアル化コンス トラクターの署名)。 このコンス トラクターが、セキュリティ チェックによって保護されていないが、型の標準コンス トラクターの 1 つ以上のセキュリティで保護されます。

## <a name="rule-description"></a>規則の説明
 このルールは、カスタムのシリアル化をサポートする型に関連します。 型は、実装している場合、カスタムのシリアル化をサポートしている、<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>インターフェイス。 シリアル化コンス トラクターが必要ですし、逆シリアル化、またはを使用してシリアル化されたオブジェクトを再作成するために使用、<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>メソッド。 シリアル化コンス トラクターでは、割り当て、オブジェクトを初期化します、ため、通常のコンス トラクターに存在するセキュリティ チェックをシリアル化コンス トラクターに存在する必要がありますも。 この規則に違反すると、インスタンスがそれ以外の場合に作成できませんでしたの呼び出し元は、これを行うにシリアル化コンス トラクターを使用できます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するのには、他のコンス トラクターを保護するものと同じセキュリティ要求を使用したシリアル化コンス トラクターを保護します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 ルールの違反を抑制しないでください。

## <a name="example"></a>例
 次の例では、規則に違反する型を示します。

 [!code-csharp[FxCop.Security.SerialCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SerialCtors/cs/FxCop.Security.SerialCtors.cs#1)]

## <a name="related-rules"></a>関連規則
 [CA2229: シリアル化コンストラクターを実装します](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2237: ISerializable 型を SerializableAttribute に設定します](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>関連項目
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>



