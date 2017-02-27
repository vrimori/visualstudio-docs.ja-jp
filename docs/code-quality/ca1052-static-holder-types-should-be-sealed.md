---
title: "CA1052: スタティック ホルダー型はシールされていなければなりません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "StaticHolderTypesShouldBeSealed"
  - "CA1052"
helpviewer_keywords: 
  - "CA1052"
  - "StaticHolderTypesShouldBeSealed"
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1052: スタティック ホルダー型はシールされていなければなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|StaticHolderTypesShouldBeSealed|  
|CheckId|CA1052|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 パブリック型またはプロテクト型に静的なメンバーしかなく、[sealed](/dotnet/csharp/language-reference/keywords/sealed) \([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)\) 修飾子付きで宣言されていません。  
  
## 規則の説明  
 この規則では、静的なメンバーしかない型は継承するようにデザインされていないと想定しています。このような型には、派生型でオーバーライドできる機能がないためです。  継承されることを意図していない型は、`sealed` 修飾子で基本型として使用を禁止するようにマークする必要があります。  
  
## 違反の修正方法  
 この規則違反を修正するには、型を `sealed` とマークします。  [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 以前を対象とする場合は、型を `static` とマークする方法をお勧めします。  この方法により、クラスが作成されないようにするためのプライベート コンストラクターを宣言せずに済みます。  
  
## 警告を抑制する状況  
 型を継承する場合にのみ、この規則による警告を抑制します。  `sealed` 修飾子がない場合、基本型として使用できる型と扱われます。  
  
## 違反の例  
  
### 説明  
 この規則に違反する型を次の例に示します。  
  
### コード  
 [!code-cs[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]  
  
## static 修飾子による修正  
  
### 説明  
 型を `static` 修飾子でマークすることによってこの規則の違反を修正する方法を次の例に示します。  
  
### コード  
 [!code-cs[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]  
  
## 関連規則  
 [CA1053: スタティック ホルダー型にはコンストラクターを含めません](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)