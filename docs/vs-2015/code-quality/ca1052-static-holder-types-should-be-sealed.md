---
title: 'Ca 1052: スタティック ホルダー型をシールする必要があります |Microsoft Docs'
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
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a912276f2f4008d1bea95027a5f2a1b67ff83e55
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589728"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: スタティック ホルダー型はシールされていなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 1052: スタティック ホルダー型をシールする必要があります](https://docs.microsoft.com/visualstudio/code-quality/ca1052-static-holder-types-should-be-sealed)します。

|||
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたはプロテクト型の静的メンバーのみが含まれていますで宣言されていない、[シール](http://msdn.microsoft.com/library/8e4ed5d3-10be-47db-9488-0da2008e6f3f)([NotInheritable](http://msdn.microsoft.com/library/5c4da7c9-9562-4653-a947-1972e992f9f9)) 修飾子。

## <a name="rule-description"></a>規則の説明
 このルールでは、型が派生型でオーバーライド可能な機能を備えていないため、静的メンバーのみを含む型でを継承するように設計しないことを前提としています。 継承を意図していない型をマークする必要があります、`sealed`基本データ型としての使用を禁止する修飾子。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、マークの種類は`sealed`します。 対象としている場合[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]型としてマークする方は、2.0 またはそれ以前`static`します。 この方法でクラスが作成されていることを防ぐために、プライベート コンス トラクターを宣言する必要があります。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 型が継承するように設計する場合にのみ、このルールから警告を抑制します。 ない場合、`sealed`修飾子が型が基本データ型として便利なことを示します。

## <a name="example-of-a-violation"></a>違反の例

### <a name="description"></a>説明
 次の例では、規則に違反する型を示します。

### <a name="code"></a>コード
 [!code-cpp[FxCop.Design.StaticMembers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cpp/FxCop.Design.StaticMembers.cpp#1)]
 [!code-csharp[FxCop.Design.StaticMembers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cs/FxCop.Design.StaticMembers.cs#1)]
 [!code-vb[FxCop.Design.StaticMembers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/vb/FxCop.Design.StaticMembers.vb#1)]

## <a name="fix-with-the-static-modifier"></a>Static 修飾子で修正します。

### <a name="description"></a>説明
 次の例を持つ型をマークすることでこの規則違反を修正する方法を示しています、`static`修飾子。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembersFixed/cs/FxCop.Design.StaticMembersFixed.cs#1)]

## <a name="related-rules"></a>関連規則
 [CA1053: スタティック ホルダー型にはコンストラクターを含めません](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)



