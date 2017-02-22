---
title: "CA2217: enums を FlagsAttribute に設定しません | Microsoft Docs"
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
  - "DoNotMarkEnumsWithFlags"
  - "CA2217"
helpviewer_keywords: 
  - "CA2217"
  - "DoNotMarkEnumsWithFlags"
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2217: enums を FlagsAttribute に設定しません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotMarkEnumsWithFlags|  
|CheckId|CA2217|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 外部から参照できる列挙型が <xref:System.FlagsAttribute> でマークされ、その列挙型に、2 の累乗でもその列挙型で定義されている他の値の組み合わせでもない値が 1 つ以上含まれています。  
  
## 規則の説明  
 列挙型で定義された値が 2 の累乗値または定義された値の組み合わせの場合にのみ、列挙型に <xref:System.FlagsAttribute> を指定します。  
  
## 違反の修正方法  
 この規則違反を修正するには、列挙型から <xref:System.FlagsAttribute> を削除します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 次の例に、Color という列挙型を示します。この列挙型には、値 3 が含まれます。これは、2 の累乗ではなく、また、定義された値の組み合わせでもありません。  そのため、Color 列挙型を <xref:System.FlagsAttribute> でマークすることはできません。  
  
 [!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
 [!code-cs[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
 [!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]  
  
## 使用例  
 次の例に、Days という列挙型を示します。この列挙型は、System.FlagsAttribute でマークする要件に適合しています。  
  
 [!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
 [!code-cs[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
 [!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]  
  
## 関連規則  
 [CA1027: FlagsAttribute で列挙値をマークします](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
## 参照  
 <xref:System.FlagsAttribute?displayProperty=fullName>