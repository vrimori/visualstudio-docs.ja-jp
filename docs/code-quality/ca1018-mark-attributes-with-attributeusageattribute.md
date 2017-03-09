---
title: "CA1018: 属性を AttributeUsageAttribute に設定します | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1018"
  - "MarkAttributesWithAttributeUsage"
helpviewer_keywords: 
  - "CA1018"
  - "MarkAttributesWithAttributeUsage"
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1018: 属性を AttributeUsageAttribute に設定します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAttributesWithAttributeUsage|  
|CheckId|CA1018|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 <xref:System.AttributeUsageAttribute?displayProperty=fullName> 属性が、カスタム属性にありません。  
  
## 規則の説明  
 カスタム属性を定義する場合、<xref:System.AttributeUsageAttribute> を使用してマークし、カスタム属性を適用できるソース コードの位置を示します。  属性の意味と用途によって、コード内の有効な位置が決まります。  たとえば、ライブラリに含まれる型の保守および強化を行う担当者について、識別する属性を定義し、その責任を常に型レベルに割り当てるとします。  この場合、コンパイラで、クラス、列挙体、およびインターフェイスに対してこの属性を有効にし、メソッド、イベント、またはプロパティに対してはこの属性を無効にする必要があります。  組織のポリシーと手順によって、アセンブリでこの属性が有効になるかどうかが決まります。  
  
 <xref:System.AttributeTargets?displayProperty=fullName> 列挙体で、カスタム属性を指定できる対象を定義します。  <xref:System.AttributeUsageAttribute> を省略した場合、<xref:System.AttributeTargets> 列挙体の `All` 値で定義されているように、カスタム属性はすべての対象で有効になります。  
  
## 違反の修正方法  
 この規則違反を修正するには、<xref:System.AttributeUsageAttribute> を使用して属性の対象を指定します。  次の例を参照してください。  
  
## 警告を抑制する状況  
 メッセージを除外するのではなく、この規則違反を修正してください。  属性が <xref:System.AttributeUsageAttribute> を継承する場合でも、コードの保守を簡単にするために属性を指定します。  
  
## 使用例  
 2 つの属性の定義を次の例に示します。  `BadCodeMaintainerAttribute` では誤って <xref:System.AttributeUsageAttribute> ステートメントを省略していますが、`GoodCodeMaintainerAttribute` では前述の属性を正しく実装しています。  `DeveloperName` プロパティは、デザイン規則「[CA1019: 属性引数にアクセサーを定義します](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)」に適合するために取り入れています。  
  
 [!code-cs[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]  
  
## 関連規則  
 [CA1019: 属性引数にアクセサーを定義します](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1813: シールされていない属性を使用しません](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## 参照  
 [属性](../Topic/Attributes1.md)