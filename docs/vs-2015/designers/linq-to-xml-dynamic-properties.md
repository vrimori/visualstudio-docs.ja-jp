---
title: LINQ to XML の動的プロパティ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6fce9bca76b604413dc5bd4962760ee4ce08a6ea
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790614"
---
# <a name="linq-to-xml-dynamic-properties"></a>LINQ to XML の動的プロパティ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ここでは、LINQ to XML の動的プロパティに関する参照情報について説明します。 これらのプロパティは、具体的には <xref:System.Xml.Linq.XAttribute> 名前空間の <xref:System.Xml.Linq.XElement> クラスと <xref:System.Xml.Linq> クラスによって公開されます。  
  
 「[LINQ to XML による WPF のデータ バインディングの概要](../designers/wpf-data-binding-with-linq-to-xml-overview.md)」のトピックで説明されているように、各動的プロパティには、対応する標準のパブリック プロパティやパブリック メソッドが同じクラスにあります。 ほとんどの用途では、これらの標準のメンバーを使用する必要があります。動的プロパティは、LINQ to XML のデータ バインディングのシナリオ専用に用意されています。 これらのクラスの標準のメンバーに関する詳細については、リファレンス トピックの「<xref:System.Xml.Linq.XAttribute>」および「<xref:System.Xml.Linq.XElement>」を参照してください。  
  
 このセクションの動的プロパティは、解決される値に関連して次の 2 つのカテゴリに分類されます。  
  
- 1 つの値に解決される単純なプロパティ (`Value` クラスや <xref:System.Xml.Linq.XAttribute> クラスの <xref:System.Xml.Linq.XElement> プロパティなど)。  
  
- インデクサー型に解決されるインデックス値 (<xref:System.Xml.Linq.XElement> の [Elements](../designers/elements-xelement-dynamic-property.md) プロパティや [Descendants](../designers/descendants-xelement-dynamic-property.md) プロパティなど)。 インデクサー型が目的の値やコレクションに解決されるようにするには、展開名のパラメーターを渡す必要があります。  
  
  <xref:System.Collections.Generic.IEnumerable%601> 型のインデックス値を返す動的プロパティはすべて遅延実行を使用します。 遅延実行について詳しくは、「[LINQ クエリの概要 (C#)](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8)」をご覧ください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[XAttribute クラスの動的プロパティ](../designers/xattribute-class-dynamic-properties.md)|<xref:System.Xml.Linq.XAttribute> クラスによって公開される動的プロパティの詳細情報について説明します。|  
|[XElement クラスの動的プロパティ](../designers/xelement-class-dynamic-properties.md)|<xref:System.Xml.Linq.XElement> クラスによって公開される動的プロパティの詳細情報について説明します。|  
  
## <a name="reference"></a>参照  
 <xref:System.Xml.Linq>  
  
 <xref:System.Xml.Linq.XElement?displayProperty=fullName>  
  
 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>  
  
## <a name="see-also"></a>「  
 [LINQ to XML による WPF のデータ バインディング](../designers/wpf-data-binding-with-linq-to-xml.md)   
 [LINQ to XML による WPF のデータ バインディングの概要](../designers/wpf-data-binding-with-linq-to-xml-overview.md)   
 [LINQ クエリの概要 (C#)](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8)
