---
title: "Descendants (XElement Dynamic Property) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Descendants (XElement Dynamic Property)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

現在の要素の子孫要素のうち指定された展開名に一致するすべての子孫要素を取得するためのインデクサーを取得します。  
  
## 構文  
  
```  
elem.Descendants[{namespaceName}localName]  
```  
  
## プロパティ値\/戻り値  
 `IEnumerable<XElement> Item(String expandedName)` 型のインデクサー。このインデクサーは、指定された子孫要素の展開名を受け取り、<xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` コレクション内の一致する子要素を返します。  
  
## 解説  
 このプロパティは、<xref:System.Xml.Linq.XContainer> クラスの <xref:System.Xml.Linq.XContainer.Descendants%28System.Xml.Linq.XName%29?displayProperty=fullName> メソッドに相当します。  
  
 返されるコレクション内の要素は、XML ソース ドキュメント順になります。  
  
 このプロパティは、遅延実行を使用します。  
  
## 参照  
 [XElement Class Dynamic Properties](../designers/xelement-class-dynamic-properties.md)   
 [Elements](../designers/elements-xelement-dynamic-property.md)