---
title: ': Ca 2235 すべてのシリアル化できないフィールド |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 025ee336052bdad010b55e1ba804b2bd37c7e0d7
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589801"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: すべてのシリアル化不可能なフィールドを設定します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CA2235: すべてのシリアル化不可能なフィールドをマーク](https://docs.microsoft.com/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)します。

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

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、適用、<xref:System.NonSerializedAttribute?displayProperty=fullName>属性をシリアル化可能でないフィールド。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 場合にこの規則による警告を抑制するのみ、<xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName>シリアル化および逆シリアル化するフィールドのインスタンスを利用できる型を宣言します。

## <a name="example"></a>例
 次の例では、規則に違反する型と、規則に適合する型を示します。

 [!code-csharp[FxCop.Usage.MarkNonSerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkNonSerializable/cs/FxCop.Usage.MarkNonSerializable.cs#1)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkNonSerializable/vb/FxCop.Usage.MarkNonSerializable.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA2236: ISerializable 型で基本クラス メソッドを呼び出します](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: ISerializable を正しく実装します](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: シリアル化コンストラクターを実装します](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: シリアル化メソッドを正しく実装します](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2237: ISerializable 型を SerializableAttribute に設定します](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: オプションのフィールドに逆シリアル化メソッドを指定します](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: シリアル化コンストラクターをセキュリティで保護します](../code-quality/ca2120-secure-serialization-constructors.md)



