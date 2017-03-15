---
title: "CA1501: 継承を使用しすぎないでください | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1501"
  - "AvoidExcessiveInheritance"
helpviewer_keywords: 
  - "AvoidExcessiveInheritance"
  - "CA1501"
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1501: 継承を使用しすぎないでください
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveInheritance|  
|CheckId|CA1501|  
|分類|Microsoft.Maintainability|  
|互換性に影響する変更点|あり|  
  
## 原因  
 型が、その継承階層内の 5 つ以上深いレベルにあります。  
  
## 規則の説明  
 深いレベルで入れ子にされた型の確認、理解、および保守は困難です。  この規則は、分析を同じモジュール内の階層に限定します。  
  
## 違反の修正方法  
 この規則違反を修正するには、継承階層内でより浅いレベルの基本型から型を派生させるか、中間の基本型をいくつか削除します。  
  
## 警告を抑制する状況  
 この規則による警告を抑制しても安全です。  ただし、コードの管理が難しくなる場合があります。  基本型の参照可能範囲によっては、この規則違反の修正が互換性に影響を与える可能性があるので、注意してください。  たとえば、パブリックな基本型を削除することは、互換性に影響を与える変更点です。  
  
## 使用例  
 この規則に違反する型を次の例に示します。  
  
 [!code-cs[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]