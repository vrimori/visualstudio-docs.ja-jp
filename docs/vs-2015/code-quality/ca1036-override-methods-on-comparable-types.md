---
title: 'Ca 1036: 比較可能な型のメソッドのオーバーライド |Microsoft Docs'
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
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1069316d0a027678b1161a948765bb81f1de68de
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49202827"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: 比較可能な型でメソッドをオーバーライドします
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 パブリックまたはプロテクト型の実装、<xref:System.IComparable?displayProperty=fullName>インターフェイスをオーバーライドしない<xref:System.Object.Equals%2A?displayProperty=fullName>または等しいかどうか、非等値、未満かより大きい言語固有の演算子をオーバー ロードしません。 ルールは、型がインターフェイスの実装のみを継承する場合、違反を報告しません。

## <a name="rule-description"></a>規則の説明
 カスタムの並べ替え順序を定義する型を実装、<xref:System.IComparable>インターフェイス。 <xref:System.IComparable.CompareTo%2A>メソッドは、型の 2 つのインスタンスの正しい並べ替え順序を示す整数値を返します。 このルールは、並べ替え順を設定する種類を識別します。これは、非等値、等しいかどうかの通常の意味よりも大きい値を指定してよりは適用されないことを意味します。 実装を提供する<xref:System.IComparable>、通常必要がありますもオーバーライド<xref:System.Object.Equals%2A>と一致する値を返すように<xref:System.IComparable.CompareTo%2A>します。 オーバーライドする場合は<xref:System.Object.Equals%2A>コーディングと演算子のオーバー ロードをサポートする言語に合致する演算子も提供する必要があります<xref:System.Object.Equals%2A>します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、オーバーライド<xref:System.Object.Equals%2A>します。 使用するプログラミング言語では、演算子のオーバー ロードをサポートする場合は、次の演算子を指定します。

-   op_Equality

-   op_Inequality

-   op_LessThan

-   op_GreaterThan

 これらの演算子を表すために使用されるトークンは次のように、c# で: = =、! =、 \<、および >。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 演算子がないために違反が発生し、プログラミング言語が演算子のオーバー ロードをサポートしていない Visual Basic .NET を使用した場合と同様、この規則による警告を抑制しても安全になります。 Op_Equality 演算子を実装するいると判断した場合は、アプリケーションのコンテキストで意味を成しません以外の等値演算子を発生させるときにこの規則からの警告を抑制しても安全です。 ただしは常に op_Equality 経由で、Object.Equals をオーバーライドする場合は、演算子を = =。

## <a name="example"></a>例
 次の例には、正しく実装する型が含まれています。<xref:System.IComparable>します。 コードのコメントを関連するさまざまなルールを満たすメソッドを識別する<xref:System.Object.Equals%2A>と<xref:System.IComparable>インターフェイス。

 [!code-csharp[FxCop.Design.IComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IComparable/cs/FxCop.Design.IComparable.cs#1)]

## <a name="example"></a>例
 次のアプリケーションの動作をテストする、<xref:System.IComparable>前に示した実装します。

 [!code-csharp[FxCop.Design.TestIComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestIComparable/cs/FxCop.Design.TestIComparable.cs#1)]

## <a name="see-also"></a>関連項目
 <xref:System.IComparable?displayProperty=fullName> <xref:System.Object.Equals%2A?displayProperty=fullName>
 [等値演算子](http://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)



