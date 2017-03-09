---
title: "CA1714: フラグ列挙は、複数形の名前を含んでいなければなりません | Microsoft Docs"
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
  - "FlagsEnumsShouldHavePluralNames"
  - "CA1714"
helpviewer_keywords: 
  - "CA1714"
  - "FlagsEnumsShouldHavePluralNames"
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1714: フラグ列挙は、複数形の名前を含んでいなければなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|FlagsEnumsShouldHavePluralNames|  
|CheckId|CA1714|  
|分類|Microsoft.Naming|  
|互換性に影響する変更点|あり|  
  
## 原因  
 パブリック列挙体に <xref:System.FlagsAttribute?displayProperty=fullName> があり、その名前の末尾に ”s” がありません。  
  
## 規則の説明  
 <xref:System.FlagsAttribute> でマークされた型は複数形の名前を持ちます。これは、この属性が複数の値を指定できることを示すからです。  たとえば、曜日を定義する列挙体があり、複数の曜日を指定できるアプリケーションでの使用を目的としているとします。  このような列挙体には <xref:System.FlagsAttribute> を追加し、名前は ”Days” などとします。  同じような列挙体で、1 つの曜日しか指定できない場合は、この属性を追加せず、名前は ”Day” などとします。  
  
 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。  これにより、新しいソフトウェア ライブラリを習得するまでの時間を短縮でき、マネージ コード開発の専門家によってライブラリが開発されたという信頼を顧客に与えることができます。  
  
## 違反の修正方法  
 列挙体の名前を複数形の語にします。同時に複数の値を指定できない列挙体の場合は <xref:System.FlagsAttribute> 属性を削除します。  
  
## 警告を抑制する状況  
 名前が複数形の語であっても末尾に ”s” がない場合は、違反を抑制しても安全です。  たとえば、上記の複数の曜日を指定できる列挙体の名前を "DaysOfTheWeek" とした場合、規則のロジックには違反しますが、違反の報告を受ける意味はありません。  このような違反は抑制する必要があります。  
  
## 関連規則  
 [CA1027: FlagsAttribute で列挙値をマークします](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217: enums を FlagsAttribute に設定しません](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## 参照  
 <xref:System.FlagsAttribute?displayProperty=fullName>   
 [列挙型デザイン](../Topic/Enum%20Design.md)