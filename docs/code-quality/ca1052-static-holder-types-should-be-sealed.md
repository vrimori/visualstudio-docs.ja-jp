---
title: 'CA1052: スタティック ホルダー型はシールされていなければなりません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bc264b9e47fe9169c0b1ad9d3257323c437620f7
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550428"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: スタティック ホルダー型はシールされていなければなりません

|||
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたはプロテクト型の静的メンバーのみが含まれていますで宣言されていない、[シール](/dotnet/csharp/language-reference/keywords/sealed)([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) 修飾子。

## <a name="rule-description"></a>規則の説明
 このルールでは、型が派生型でオーバーライド可能な機能を備えていないため、静的メンバーのみを含む型でを継承するように設計しないことを前提としています。 継承を意図していない型をマークする必要があります、`sealed`基本データ型としての使用を禁止する修飾子。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、マークの種類は`sealed`します。 対象としている場合[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]型としてマークする方は、2.0 以降、`static`します。 この方法でクラスが作成されていることを防ぐために、プライベート コンス トラクターを宣言する必要があります。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 型が継承するように設計する場合にのみ、このルールから警告を抑制します。 ない場合、`sealed`修飾子が型が基本データ型として便利なことを示します。

## <a name="example-of-a-violation"></a>違反の例

### <a name="description"></a>説明
 次の例では、規則に違反する型を示します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]

## <a name="fix-with-the-static-modifier"></a>Static 修飾子で修正します。

### <a name="description"></a>説明
 次の例を持つ型をマークすることでこの規則違反を修正する方法を示しています、`static`修飾子。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]

## <a name="related-rules"></a>関連するルール
 [CA1053: スタティック ホルダー型にはコンストラクターを含めません](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
