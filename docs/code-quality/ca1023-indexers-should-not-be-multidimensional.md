---
title: "CA1023: インデクサーを多次元にすることはできません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IndexersShouldNotBeMultidimensional"
  - "CA1023"
helpviewer_keywords: 
  - "CA1023"
  - "IndexersShouldNotBeMultidimensional"
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA1023: インデクサーを多次元にすることはできません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IndexersShouldNotBeMultidimensional|  
|CheckId|CA1023|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 パブリック型またはプロテクト型に、複数のインデックスを使用するパブリック インデクサーまたはプロテクト インデクサーが含まれます。  
  
## 規則の説明  
 インデクサー、言い換えるとインデックスされたプロパティでは、インデックスを 1 つだけ使用します。  多次元のインデクサーがあると、ライブラリの操作性が著しく悪くなることがあります。  デザインで複数のインデックスが必要な場合は、その型が論理的なデータ ストアを表しているかどうかを再確認します。  論理データ メンバーでない場合は、メソッドを使用します。  
  
## 違反の修正方法  
 この規則違反を修正するには、設計を変更し、整数型または文字列型のインデックスを 1 つだけ使用するか、インデクサーではなくメソッドを使用するようにします。  
  
## 警告を抑制する状況  
 標準的ではないインデクサーの必要性を十分に考慮したうえで、この規則による警告を抑制します。  
  
## 使用例  
 規則に違反している多次元のインデクサーを持つ型 `DayOfWeek03` を次の例に示します。  このインデクサーはある種の変換のように見えます。そのため、メソッドとして公開する方が適切です。  この型は、規則に適合するように `RedesignedDayOfWeek03` で再デザインしました。  
  
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
 [!code-cs[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]  
  
## 関連規則  
 [CA1043: インデクサーには整数または文字列引数を使用します](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)  
  
 [CA1024: 適切な場所にプロパティを使用します](../code-quality/ca1024-use-properties-where-appropriate.md)