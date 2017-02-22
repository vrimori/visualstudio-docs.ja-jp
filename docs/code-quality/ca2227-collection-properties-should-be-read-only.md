---
title: "CA2227: Collection プロパティは読み取り専用でなければなりません | Microsoft Docs"
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
  - "CA2227"
  - "CollectionPropertiesShouldBeReadOnly"
helpviewer_keywords: 
  - "CA2227"
  - "CollectionPropertiesShouldBeReadOnly"
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2227: Collection プロパティは読み取り専用でなければなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CollectionPropertiesShouldBeReadOnly|  
|CheckId|CA2227|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|あり|  
  
## 原因  
 外部で参照できる書き込み可能なプロパティが、<xref:System.Collections.ICollection?displayProperty=fullName> を実装する型になっています。  配列、インデクサー \('Item' という名前が付くプロパティ\)、およびアクセス許可セットは、この規則では無視されます。  
  
## 規則の説明  
 書き込み可能なコレクション プロパティにより、ユーザーはコレクションを完全に異なるコレクションで置換できます。  読み取り専用プロパティは、コレクションを置換できないようにしますが、個別のメンバーが設定されることは回避できません。  コレクションの置換が目的である場合は、適切なデザイン パターンとは、すべての要素をコレクションから削除するメソッドおよびコレクションを再構築するメソッドを含めることです。  このパターンの例については、<xref:System.Collections.ArrayList?displayProperty=fullName> クラスの <xref:System.Collections.ArrayList.Clear%2A> メソッドおよび <xref:System.Collections.ArrayList.AddRange%2A> メソッドのトピックを参照してください。  
  
 バイナリ シリアル化および XML シリアル化は、両方ともコレクションである読み取り専用プロパティをサポートします。  <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> クラスには、<xref:System.Collections.ICollection> および <xref:System.Collections.IEnumerable?displayProperty=fullName> を実装する型に関して、シリアル化可能にするための 固有の要件があります。  
  
## 違反の修正方法  
 この規則の違反を修正するには、プロパティを読み取り専用にします。また、デザイン上必要な場合は、コレクションの追加と再構築を行うメソッドを追加します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 次の例は、書き込み可能なコレクション プロパティを持つ型と、コレクションを直接置換する方法を示しています。  さらに、`Clear` メソッドおよび `AddRange` メソッドを使用して読み取り専用コレクションを置換する適切な方法も示しています。  
  
 [!code-cs[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]  
  
## 関連規則  
 [CA1819: プロパティは、配列を返すことはできません](../code-quality/ca1819-properties-should-not-return-arrays.md)