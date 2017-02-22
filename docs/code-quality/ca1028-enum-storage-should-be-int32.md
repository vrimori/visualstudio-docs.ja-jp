---
title: "CA1028: 列挙ストレージは Int32 でなければなりません | Microsoft Docs"
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
  - "CA1028"
  - "EnumStorageShouldBeInt32"
helpviewer_keywords: 
  - "CA1028"
  - "EnumStorageShouldBeInt32"
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1028: 列挙ストレージは Int32 でなければなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|EnumStorageShouldBeInt32|  
|CheckId|CA1028|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 パブリックの列挙体の基になる型が、<xref:System.Int32?displayProperty=fullName> ではありません。  
  
## 規則の説明  
 列挙型は、関連する名前付き定数が複数定義された値型です。  既定で、<xref:System.Int32?displayProperty=fullName> データ型は、定数値を格納するために使用されます。  この基になる型を変更できる場合でも、ほとんどの場合、変更する必要はありませんし、推奨されません。  <xref:System.Int32> よりも小さいデータ型を使用しても、パフォーマンスはあまり向上しません。  既定のデータ型を使用できない場合、Common Language System \(CLS\) 準拠の整数型、<xref:System.Byte>、<xref:System.Int16>、<xref:System.Int32>、<xref:System.Int64> のいずれかを使用して、列挙値のすべてが CLS 準拠のプログラミング言語で表すことができるようにします。  
  
## 違反の修正方法  
 この規則違反を修正するには、サイズや互換性の問題がなければ、<xref:System.Int32> を使用します。  <xref:System.Int32> のサイズでは値を格納できない場合、<xref:System.Int64> を使用します。  下位互換性のために小さなデータ型が必要な場合、<xref:System.Byte> または <xref:System.Int16> を使用します。  
  
## 警告を抑制する状況  
 下位互換性の問題で必要な場合にのみ、この規則による警告を抑制します。  一般に、アプリケーションでは、この規則に準拠しないことによって問題は発生しません。  言語の相互運用性が必要なライブラリの場合、この規則に準拠しないことで、ライブラリを使用するときに悪影響が及ぶ可能性があります。  
  
## 違反の例  
  
### 説明  
 基になるデータ型に推奨される型を使用していない 2 つの列挙型を次の例に示します。  
  
### コード  
 [!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
 [!code-cs[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]  
  
## 修正方法の例  
  
### 説明  
 基になるデータ型を <xref:System.Int32> に変更することによって上記の違反を修正するコード例を次に示します。  
  
### コード  
 [!code-cs[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]  
  
## 関連規則  
 [CA1008: Enums は 0 値を含んでいなければなりません](../code-quality/ca1008-enums-should-have-zero-value.md)  
  
 [CA1027: FlagsAttribute で列挙値をマークします](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217: enums を FlagsAttribute に設定しません](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1700: enum 値に 'Reserved' という名前を指定しません](../code-quality/ca1700-do-not-name-enum-values-reserved.md)  
  
 [CA1712: enum 値を型名のプレフィックスにしません](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
## 参照  
 <xref:System.Byte?displayProperty=fullName>   
 <xref:System.Int16?displayProperty=fullName>   
 <xref:System.Int32?displayProperty=fullName>   
 <xref:System.Int64?displayProperty=fullName>