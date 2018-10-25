---
title: 'CA2240: 実装 ISerializable 正しく |Microsoft Docs'
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
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bf9578d12a9d89a5c328cf15c1c5a7becef12cd7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888931"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: ISerializable を正しく実装します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 割り当てることは、外部から参照できる型は、<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>インターフェイスと、次の条件のいずれかが true:

-   型の継承がオーバーライドしません、<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>メソッドと型の宣言でマークされていないインスタンス フィールド、<xref:System.NonSerializedAttribute?displayProperty=fullName>属性。

-   型がシールされていないと、型を実装、<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>が外部で表示され、オーバーライド可能なメソッドです。

## <a name="rule-description"></a>規則の説明
 インスタンス フィールドを継承する型で宣言されている、<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>インターフェイスは、自動的にシリアル化プロセスには含まれません。 フィールドは、型を実装する必要があります、<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>メソッドとシリアル化コンス トラクター。 フィールドをシリアル化する必要がありますしない場合は、適用、<xref:System.NonSerializedAttribute>意思決定を明示的に示すフィールドに属性します。

 シールされていない、実装の種類で、<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>メソッドを外部から参照可能にする必要があります。 そのため、メソッドは、派生型は、呼び出すことができ、オーバーライド可能なは。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するように、<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>メソッドをオーバーライドできるすべてのインスタンス フィールドをシリアル化プロセスに含まれるかで明示的にマークされていることを確認して、<xref:System.NonSerializedAttribute>属性。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、ルールに違反している 2 つのシリアル化可能な型を示します。

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cpp/FxCop.Usage.ImplementISerializableCorrectly.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cs/FxCop.Usage.ImplementISerializableCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/vb/FxCop.Usage.ImplementISerializableCorrectly.vb#1)]

## <a name="example"></a>例
 次の例は、[ISerializable.GetObjectData] の上書き可能な実装を提供して前の 2 つの違反を修正 (<!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  -->) Book クラスの実装を提供すること、および<!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  -->ライブラリ クラス。

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cpp/FxCop.Usage.ImplementISerializableCorrectly2.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cs/FxCop.Usage.ImplementISerializableCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/vb/FxCop.Usage.ImplementISerializableCorrectly2.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA2236: ISerializable 型で基本クラス メソッドを呼び出します](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2229: シリアル化コンストラクターを実装します](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: シリアル化メソッドを正しく実装します](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: すべてのシリアル化不可能なフィールドを設定します](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: ISerializable 型を SerializableAttribute に設定します](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: オプションのフィールドに逆シリアル化メソッドを指定します](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: シリアル化コンストラクターをセキュリティで保護します](../code-quality/ca2120-secure-serialization-constructors.md)



