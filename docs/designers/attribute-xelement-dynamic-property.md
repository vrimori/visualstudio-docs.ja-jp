---
title: "Attribute (XElement Dynamic Property) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Attribute (XElement Dynamic Property)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定された展開名に対応する属性のインスタンスの取得に使用するインデクサーを取得します。  
  
## 構文  
  
```  
elem.Attribute[{namespaceName}attribName]  
```  
  
## プロパティ値\/戻り値  
 `XAttribute Item(String expandedName)` 型のインデクサー。このインデクサーは、指定された属性の展開名を受け取り、対応する <xref:System.Xml.Linq.XAttribute> を返します。指定された名前を持つ属性がない場合は、`null` を返します。  
  
## 解説  
 このプロパティは、<xref:System.Xml.Linq.XElement?displayProperty=fullName> クラスの <xref:System.Xml.Linq.XElement.Attribute%2A> メソッドに相当します。  
  
## 参照  
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>   
 [XElement Class Dynamic Properties](../designers/xelement-class-dynamic-properties.md)   
 [Value](../designers/value-xattribute-dynamic-property.md)