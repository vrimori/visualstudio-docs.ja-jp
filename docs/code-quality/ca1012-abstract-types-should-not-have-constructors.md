---
title: "CA1012: 抽象型にはコンストラクターを含めません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AbstractTypesShouldNotHaveConstructors"
  - "CA1012"
helpviewer_keywords: 
  - "CA1012"
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
caps.latest.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 25
---
# CA1012: 抽象型にはコンストラクターを含めません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AbstractTypesShouldNotHaveConstructors|  
|CheckId|CA1012|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|なし|  
  
## 原因  
 パブリック型が抽象型で、パブリック コンストラクターが含まれます。  
  
## 規則の説明  
 抽象型上のコンストラクターは、派生型からのみ呼び出すことができます。  パブリック コンストラクターで型のインスタンスが作成され、抽象型のインスタンスは自分で作成できないため、パブリック コンストラクターが含まれる抽象型のデザインは不適切になります。  
  
## 違反の修正方法  
 この規則違反を修正するには、コンストラクターをプロテクトにするか、抽象型を宣言しないようにします。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  抽象型にはパブリック コンストラクターが含まれています。  
  
## 使用例  
 この規則に違反する抽象型を使用したコード例を次に示します。  
  
 [!code-vb[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_1.vb)]
 [!code-cs[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_1.cs)]  
  
## 使用例  
 コンストラクターのアクセシビリティを `public` から `protected` に変更することによって上記の違反を修正するコード例を次に示します。  
  
 [!code-cs[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_2.cs)]
 [!code-vb[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_2.vb)]