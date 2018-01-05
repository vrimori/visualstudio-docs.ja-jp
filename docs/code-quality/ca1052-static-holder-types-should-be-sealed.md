---
title: "Ca 1052: スタティック ホルダー型はシールする必要があります |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d9ce807aca8b28a279a3a423802196e710f63dea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: スタティック ホルダー型はシールされていなければなりません
|||  
|-|-|  
|TypeName|StaticHolderTypesShouldBeSealed|  
|CheckId|CA1052|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 パブリックまたはプロテクト型は、静的メンバーのみが含まれておりで宣言されていない、[シール](/dotnet/csharp/language-reference/keywords/sealed)([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) 修飾子。  
  
## <a name="rule-description"></a>規則の説明  
 このルールでは、静的メンバーだけを含む型はいないに設計されているを継承する型が派生型でオーバーライド可能な機能を提供しないので前提としています。 継承を意図していない型をマークする必要があります、`sealed`基本型としての使用を禁止する修飾子です。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、マークの種類は`sealed`します。 対象としている場合[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]と型を示すためにより適切な方法は、2.0 またはそれ以降、`static`です。 この方法で、クラスが作成されないように、プライベート コンス トラクターを宣言する必要があります。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 型を継承する場合にのみ、この規則による警告を抑制します。 ない場合、`sealed`修飾子は、型が基本型として便利であるを提案します。  
  
## <a name="example-of-a-violation"></a>違反の例  
  
### <a name="description"></a>説明  
 次の例は、規則に違反する型を示しています。  
  
### <a name="code"></a>コード  
 [!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]  
  
## <a name="fix-with-the-static-modifier"></a>Static 修飾子での解決します。  
  
### <a name="description"></a>説明  
 次の例を持つ型をマークすることによってこの規則違反の修正方法を示しています、`static`修飾子です。  
  
### <a name="code"></a>コード  
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]  
  
## <a name="related-rules"></a>関連規則  
 [CA1053: スタティック ホルダー型にはコンストラクターを含めません](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
