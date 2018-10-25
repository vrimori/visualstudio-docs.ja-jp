---
title: '2218: オーバーライド GetHashCode を Equals をオーバーライド |Microsoft Docs'
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
- CA2218
- OverrideGetHashCodeOnOverridingEquals
helpviewer_keywords:
- OverrideGetHashCodeOnOverridingEquals
- CA2218
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bc9e72639e123e0a99c4423b460bc4122995971c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881912"
---
# <a name="ca2218-override-gethashcode-on-overriding-equals"></a>CA2218: オーバーライドする Equals で GetHashCode をオーバーライドします
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideGetHashCodeOnOverridingEquals|
|CheckId|CA2218|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 パブリック型のオーバーライド<xref:System.Object.Equals%2A?displayProperty=fullName>がオーバーライドしません<xref:System.Object.GetHashCode%2A?displayProperty=fullName>します。

## <a name="rule-description"></a>規則の説明
 <xref:System.Object.GetHashCode%2A> ハッシュ アルゴリズムやハッシュ テーブルなどのデータ構造に適していますが、現在のインスタンスに基づいて、値を返します。 同じ種類し、が等しい 2 つのオブジェクトには、次の型のインスタンスが正しく動作する同じハッシュ コードを返す必要があります。

-   <xref:System.Collections.Hashtable?displayProperty=fullName>

-   <xref:System.Collections.SortedList?displayProperty=fullName>

-   <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>

-   <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName>

-   <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>

-   <xref:System.Collections.Specialized.HybridDictionary?displayProperty=fullName>

-   <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>

-   <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>

-   実装する型 <xref:System.Collections.Generic.IEqualityComparer%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、実装を提供<xref:System.Object.GetHashCode%2A>します。 同じ型のオブジェクトのペアの場合、実装が同じ値を返すことを確認する必要がありますの実装<xref:System.Object.Equals%2A>返します`true`ペアを指定します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="class-example"></a>クラスの例

### <a name="description"></a>説明
 次の例では、この規則に違反するためのクラス (参照型) を示します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Usage.GetHashCodeErrorClass#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeErrorClass/cs/FxCop.Usage.GetHashCodeErrorClass.cs#1)]

### <a name="comments"></a>コメント
 次の例では、オーバーライドすることで、違反を修正する<xref:System.Object.GetHashCode>します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Usage.GetHashCodeFixedClass#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeFixedClass/cs/FxCop.Usage.GetHashCodeFixedClass.cs#1)]

## <a name="structure-example"></a>構造の例

### <a name="description"></a>説明
 次の例では、この規則に違反する構造体 (値型) を示します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Usage.GetHashCodeErrorStruct#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeErrorStruct/cs/FxCop.Usage.GetHashCodeErrorStruct.cs#1)]

### <a name="comments"></a>コメント
 次の例では、オーバーライドすることで、違反を修正する<xref:System.Object.GetHashCode>します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Usage.GetHashCodeFixedStruct#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeFixedStruct/cs/FxCop.Usage.GetHashCodeFixedStruct.cs#1)]

## <a name="related-rules"></a>関連規則
 [CA1046: 参照型で、演算子 equals をオーバーロードしないでください](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: 演算子オーバーロードには名前付けされた代替が存在します](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: 演算子は対称型オーバーロードを含まなければなりません](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: オーバーロードする演算子 equals で Equals をオーバーライドします](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231: ValueType.Equals のオーバーライドで、演算子 equals をオーバーロードします](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

## <a name="see-also"></a>関連項目

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- <xref:System.Object.GetHashCode%2A?displayProperty=fullName>
- <xref:System.Collections.Hashtable?displayProperty=fullName>
- [等値演算子](http://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)