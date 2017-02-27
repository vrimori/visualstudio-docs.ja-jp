---
title: "CA1027: FlagsAttribute で列挙値をマークします | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MarkEnumsWithFlags"
  - "CA1027"
helpviewer_keywords: 
  - "CA1027"
  - "MarkEnumsWithFlags"
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1027: FlagsAttribute で列挙値をマークします
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkEnumsWithFlags|  
|CheckId|CA1027|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|なし|  
  
## 原因  
 パブリック列挙型の値が、2 の累乗か、その列挙型で定義された他の値の組み合わせです。また、<xref:System.FlagsAttribute?displayProperty=fullName> 属性が存在しません。  誤った規則違反のレポートを減らすために、連続する値のある列挙型の違反はレポートされません。  
  
## 規則の説明  
 列挙型は、関連する名前付き定数が複数定義された値型です。  名前付き定数を有意に結合できる場合、列挙型に <xref:System.FlagsAttribute> を適用します。  たとえば、使用できる曜日リソースを追跡するアプリケーションで、曜日の列挙値があるとします。  <xref:System.FlagsAttribute> がある列挙値で各リソースの可用性をエンコーディングすると、どのような曜日の組み合わせでも、表現できます。  この属性がないと、曜日の 1 日しか表現できません。  
  
 結合できる列挙値がフィールドに格納されている場合、個々の列挙値は、そのフィールド内のビット グループとして扱われます。  そのため、このようなフィールドは*ビットフィールド*と呼ばれることもあります。  1 つのビット フィールドに格納するために列挙値を結合するには、ブール型の条件演算子を使用します。  ビット フィールドをテストして、特定の列挙値が存在するかどうかを判断するには、ブール型の論理演算子を使用します。  ビット フィールドで結合された列挙値の格納と取得を正しく行うには、列挙値に定義する個々の値を 2 の累乗にする必要があります。  そうしないと、ブール型の論理演算子では、そのフィールドに格納されている個々の列挙値を抽出できなくなります。  
  
## 違反の修正方法  
 この規則違反を修正するには、列挙型に <xref:System.FlagsAttribute> を追加します。  
  
## 警告を抑制する状況  
 列挙値を結合できるようにしない場合は、この規則による警告を抑制します。  
  
## 使用例  
 次の例で、`DaysEnumNeedsFlags` は <xref:System.FlagsAttribute> を使用する要件に適合していますが、実際には使用していません。  `ColorEnumShouldNotHaveFlag` 列挙体に 2 の累乗の値はありませんが、<xref:System.FlagsAttribute> が誤って指定されています。  これは規則「[CA2217: enums を FlagsAttribute に設定しません](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)」に違反しています。  
  
 [!CODE [FxCop.Design.EnumFlags#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.EnumFlags#1)]  
  
## 関連規則  
 [CA2217: enums を FlagsAttribute に設定しません](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## 参照  
 <xref:System.FlagsAttribute?displayProperty=fullName>