---
title: "Element (XElement Dynamic Property) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "XElement.Element"
apitype: "Assembly"
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Element (XElement Dynamic Property)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定された展開名に対応する子要素のインスタンスを取得するためのインデクサーを取得します。  
  
## 構文  
  
```  
elem.Element[{namespaceName}localName]  
```  
  
## プロパティ値\/戻り値  
 `XElement Item(String expandedName)` 型のインデクサー。このインデクサーは、展開名のパラメーターを取得し、対応する <xref:System.Xml.Linq.XElement> を返します。指定された名前を持つ要素がない場合は、`null` を返します。  
  
## 解説  
 このプロパティは、<xref:System.Xml.Linq.XContainer?displayProperty=fullName> クラスの <xref:System.Xml.Linq.XContainer.Element%2A> メソッドに相当します。  
  
## 参照  
 <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>   
 [XElement Class Dynamic Properties](../designers/xelement-class-dynamic-properties.md)   
 [Elements](../designers/elements-xelement-dynamic-property.md)