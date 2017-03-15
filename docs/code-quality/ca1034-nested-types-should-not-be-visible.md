---
title: "CA1034: 入れ子にされた型を参照可能にすることはできません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "NestedTypesShouldNotBeVisible"
  - "CA1034"
helpviewer_keywords: 
  - "NestedTypesShouldNotBeVisible"
  - "CA1034"
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1034: 入れ子にされた型を参照可能にすることはできません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|NestedTypesShouldNotBeVisible|  
|CheckId|CA1034|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 外部から参照できる型に、外部から参照できる型宣言があります。  入れ子にされた列挙およびプロテクト型には、この規則は適用されません。  
  
## 規則の説明  
 入れ子にされた型とは、別の型のスコープ内で宣言された型のことです。  入れ子にされた型は、含まれる型のプライベート実装の詳細をカプセル化するときに便利です。  このような用途なので、入れ子にされた型は外部から参照できないようにします。  
  
 論理的なグループ化や、名前の衝突を回避する目的では、外部から参照できる入れ子にされた型を使用しないでください。代わりに、名前空間を使用します。  
  
 入れ子にされた型には、メンバーのアクセシビリティという概念が含まれますが、プログラマによっては、この概念を明確に理解していない場合もあります。  
  
 プロテクト型はサブクラスで使用でき、入れ子にされた型は高度なカスタマイズ シナリオで使用できます。  
  
## 違反の修正方法  
 入れ子にされた型が外部から参照できなくてもよい場合は、型のアクセシビリティを変更します。  または、入れ子にされた型を親の型から削除します。  型を分類するために入れ子にした場合、入れ子にするのではなく、名前空間を使用して階層構造を作成します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 この規則に違反する型を次の例に示します。  
  
 [!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
 [!code-cs[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]