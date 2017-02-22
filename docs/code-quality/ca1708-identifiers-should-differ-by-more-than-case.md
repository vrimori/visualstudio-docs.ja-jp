---
title: "CA1708: 識別子は、大文字と小文字の区別以外にも相違していなければなりません | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldDifferByMoreThanCase"
  - "CA1708"
helpviewer_keywords: 
  - "CA1708"
  - "IdentifiersShouldDifferByMoreThanCase"
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1708: 識別子は、大文字と小文字の区別以外にも相違していなければなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldDifferByMoreThanCase|  
|CheckId|CA1708|  
|分類|Microsoft.Naming|  
|互換性に影響する変更点|あり|  
  
## 原因  
 型、メンバー、パラメーター、または完全修飾名前空間で、名前の大文字\/小文字のみが異なるものが 2 つあります。  
  
## 規則の説明  
 名前空間、型、メンバー、およびパラメーターの各識別子は、大文字\/小文字以外のみでは区別できません。共通言語ランタイムを対象とする言語は、大文字と小文字を区別する必要はないためです。  たとえば、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] は広く使用されていますが、大文字と小文字を区別しない言語です。  
  
 この規則は、パブリックに参照可能なメンバーのみに適用されます。  
  
## 違反の修正方法  
 大文字と小文字を区別しない方法で、他の識別子と比較したときに一意になる名前を選択します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] で使用できるすべての言語で、ライブラリを使用できなくなることがあります。  
  
## 違反の例  
 この規則に違反する場合を次の例に示します。  
  
 [!code-cs[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]  
  
## 関連規則  
 [CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)