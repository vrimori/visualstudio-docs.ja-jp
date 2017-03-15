---
title: "CA1813: シールされていない属性を使用しません | Microsoft Docs"
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
  - "CA1813"
  - "AvoidUnsealedAttributes"
helpviewer_keywords: 
  - "AvoidUnsealedAttributes"
  - "CA1813"
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1813: シールされていない属性を使用しません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidUnsealedAttributes|  
|CheckId|CA1813|  
|分類|Microsoft.Performance|  
|互換性に影響する変更点|あり|  
  
## 原因  
 <xref:System.Attribute?displayProperty=fullName> から継承されたパブリック型が抽象型ではなく、シールされていません \(Visual Basic では `NotInheritable`\)。  
  
## 規則の説明  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] クラス ライブラリには、カスタム属性を取得するメソッドが用意されています。  既定で、このようなメソッドでは属性の継承階層が検索されます。たとえば、<xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> では、指定した属性型、または指定した属性型を拡張する属性型が検索されます。  属性をシールすると、継承階層の全体が検索されなくなるため、パフォーマンスが向上します。  
  
## 違反の修正方法  
 この規則違反を修正するには、属性型をシールするか、抽象型にします。  
  
## 警告を抑制する状況  
 この規則による警告を抑制しても安全です。  属性の階層構造を定義していて属性をシールできない場合、または抽象型にできない場合にのみ、除外します。  
  
## 使用例  
 この規則に適合するカスタム属性を次の例に示します。  
  
 [!code-cs[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]  
  
## 関連規則  
 [CA1019: 属性引数にアクセサーを定義します](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1018: 属性を AttributeUsageAttribute に設定します](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)  
  
## 参照  
 [属性](../Topic/Attributes1.md)