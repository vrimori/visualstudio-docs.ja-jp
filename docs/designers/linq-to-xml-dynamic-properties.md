---
title: "LINQ to XML Dynamic Properties | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# LINQ to XML Dynamic Properties
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ここでは、LINQ to XML の動的プロパティに関する参照情報について説明します。これらのプロパティは、具体的には <xref:System.Xml.Linq> 名前空間の <xref:System.Xml.Linq.XAttribute> クラスと <xref:System.Xml.Linq.XElement> クラスによって公開されます。  
  
 「[LINQ to XML による WPF のデータ バインドの概要](../designers/wpf-data-binding-with-linq-to-xml-overview.md)」で説明されているように、各動的プロパティには、対応する標準のパブリック プロパティやパブリック メソッドが同じクラスにあります。ほとんどの用途では、これらの標準のメンバーを使用する必要があります。動的プロパティは、LINQ to XML のデータ バインドのシナリオ専用に用意されています。これらのクラスの標準のメンバーに関する詳細については、リファレンス トピックの「<xref:System.Xml.Linq.XAttribute>」および「<xref:System.Xml.Linq.XElement>」を参照してください。  
  
 このセクションの動的プロパティは、解決される値に関連して次の 2 つのカテゴリに分類されます。  
  
-   1 つの値に解決される単純なプロパティ \(<xref:System.Xml.Linq.XAttribute> クラスや <xref:System.Xml.Linq.XElement> クラスの `Value` プロパティなど\)。  
  
-   インデクサー型に解決されるインデックス値 \(<xref:System.Xml.Linq.XElement> の [Elements](../designers/elements-xelement-dynamic-property.md) プロパティや [Descendants](../designers/descendants-xelement-dynamic-property.md) プロパティなど\)。インデクサー型が目的の値やコレクションに解決されるようにするには、展開名のパラメーターを渡す必要があります。  
  
 <xref:System.Collections.Generic.IEnumerable%601> 型のインデックス値を返す動的プロパティはすべて遅延実行を使用します。遅延実行の詳細については、「[Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)」を参照してください。  
  
## このセクションの内容  
  
|トピック|内容|  
|----------|--------|  
|[XAttribute Class Dynamic Properties](../designers/xattribute-class-dynamic-properties.md)|<xref:System.Xml.Linq.XAttribute> クラスによって公開される動的プロパティの詳細情報について説明します。|  
|[XElement Class Dynamic Properties](../designers/xelement-class-dynamic-properties.md)|<xref:System.Xml.Linq.XElement> クラスによって公開される動的プロパティの詳細情報について説明します。|  
  
## リファレンス  
 <xref:System.Xml.Linq>  
  
 <xref:System.Xml.Linq.XElement?displayProperty=fullName>  
  
 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>  
  
## 参照  
 [WPF Data Binding with LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml.md)   
 [WPF Data Binding with LINQ to XML Overview](../designers/wpf-data-binding-with-linq-to-xml-overview.md)   
 [Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)