---
title: "CA1048: Sealed 型の仮想メンバーを宣言しません | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotDeclareVirtualMembersInSealedTypes"
  - "CA1048"
helpviewer_keywords: 
  - "CA1048"
  - "DoNotDeclareVirtualMembersInSealedTypes"
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1048: Sealed 型の仮想メンバーを宣言しません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|  
|CheckId|CA1048|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 シールされているパブリック型に、`virtual` \(Visual Basic では `Overridable`\) であり final ではないメソッドが宣言されています。  デリゲート型の場合、このパターンに従いますが、この規則による違反はレポートされません。  
  
## 規則の説明  
 型でメソッドを仮想と宣言するのは、継承する型が仮想メソッドの実装をオーバーライドできるようにするためです。  定義によってシールされた型から継承することはできません。シールされた型の仮想メソッドの意味がなくなります。  
  
 Visual Basic .NET と C\# の各コンパイラでは、この規則に違反する型は許容されていません。  
  
## 違反の修正方法  
 この規則違反を修正するには、メソッドを非仮想にするか、型を継承できるようにします。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  型を現在のままにすると保守の問題が発生し、何も利点はありません。  
  
## 使用例  
 この規則に違反する型を次の例に示します。  
  
 [!CODE [FxCop.Design.SealedVirtual#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.SealedVirtual#1)]