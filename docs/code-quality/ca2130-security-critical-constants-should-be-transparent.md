---
title: "CA2130: セキュリティ上重要な定数は透過的である必要がある | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2130"
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# CA2130: セキュリティ上重要な定数は透過的である必要がある
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ConstantsShouldBeTransparent|  
|CheckId|CA2130|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## 原因  
 定数フィールドまたは列挙型のメンバーには <xref:System.Security.SecurityCriticalAttribute> が適用されています。  
  
## 規則の説明  
 実行時に検索の必要がない値がコンパイラのインライン定数に設定されているため、定数値に対して透過性は適用されません。  透過的なコードからは定数にアクセスできないとコード レビューアーが考えることがないよう、定数フィールドは透過的セキュリティなフィールドとして定義する必要があります。  
  
## 違反の修正方法  
 この規則違反を修正するには、フィールドまたは値から SecurityCritical 属性を削除します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 次の例では、列挙値 `EnumWithCriticalValues.CriticalEnumValue` と定数 `CriticalConstant` によってこの警告が発生します。  この問題を修正するには、\[`SecurityCritical`\] 属性を削除して透過的セキュリティなフィールドとして定義する必要があります。  
  
 [!code-cs[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../code-quality/codesnippet/CSharp/ca2130-security-critical-constants-should-be-transparent_1.cs)]