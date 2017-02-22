---
title: "CA1008: Enums は 0 値を含んでいなければなりません | Microsoft Docs"
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
  - "CA1008"
  - "EnumsShouldHaveZeroValue"
helpviewer_keywords: 
  - "CA1008"
  - "EnumsShouldHaveZeroValue"
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1008: Enums は 0 値を含んでいなければなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|EnumsShouldHaveZeroValue|  
|CheckId|CA1008|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|なし \- フラグではない列挙型に値 **None** を追加するよう求められる場合。あり \- すべての列挙値を名前変更または削除するよう求められる場合。|  
  
## 原因  
 <xref:System.FlagsAttribute?displayProperty=fullName> が適用されていない列挙型で、ゼロ値を持つメンバーが定義されていません。または、<xref:System.FlagsAttribute> が適用された列挙型でゼロ値を持つメンバーが定義されていますが、名前が "None" ではないか、列挙型で複数のゼロ値を持つメンバーが定義されています。  
  
## 規則の説明  
 初期化されていない列挙型の既定値は、他の値型と同様に、ゼロです。  フラグではない属性が付いた列挙型では、ゼロ値を持つメンバーを定義する必要があります。これは、既定値を有効な列挙値にするためです。  必要に応じてメンバーに "None" と名前を付けます。  それ以外の場合、最もよく使用するメンバーにゼロを割り当てます。  既定では、最初の列挙型メンバーの値が宣言で設定されない場合、値はゼロです。  
  
 <xref:System.FlagsAttribute> を適用した列挙型でゼロ値のメンバーを定義する場合、名前を "None" にして、列挙型に設定済みの値がないことを示します。  他の目的でゼロ値のメンバーを使用する方法は、<xref:System.FlagsAttribute> を使用する方法 \(メンバーで AND または OR のビット処理演算子を使用できません\) とは正反対です。  つまり、ゼロ値を割り当てるメンバーは 1 つのみにする必要があります。  フラグの属性が付けられた列挙型でゼロ値を持つメンバーが複数存在する場合、ゼロ以外のメンバーに対して、`Enum.ToString()` から不適切な値が返されます。  
  
## 違反の修正方法  
 フラグではない属性が付いた列挙型に関して、この規則違反を修正するには、ゼロ値を持つメンバーを定義します。これは互換性に影響する変更ではありません。  ゼロ値のメンバーを定義するフラグの属性が付いた列挙型の場合、このメンバーに "None" という名前を付け、ゼロ値を持つメンバーが他にも存在する場合は削除します。これは互換性に影響する変更です。  
  
## 警告を抑制する状況  
 以前に提供済みのフラグの属性が付いた列挙型の場合を除き、この規則からの警告を抑制しないでください。  
  
## 使用例  
 規則に適合する 2 つの列挙型と、規則に違反する列挙型 `BadTraceOptions` を次の例に示します。  
  
 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
 [!code-cs[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]  
  
## 関連規則  
 [CA2217: enums を FlagsAttribute に設定しません](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1700: enum 値に 'Reserved' という名前を指定しません](../code-quality/ca1700-do-not-name-enum-values-reserved.md)  
  
 [CA1712: enum 値を型名のプレフィックスにしません](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
 [CA1028: 列挙ストレージは Int32 でなければなりません](../code-quality/ca1028-enum-storage-should-be-int32.md)  
  
 [CA1027: FlagsAttribute で列挙値をマークします](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
## 参照  
 <xref:System.Enum?displayProperty=fullName>