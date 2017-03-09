---
title: "Xml (XElement Dynamic Property) | Microsoft Docs"
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
  - "XElement.Xml"
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Xml (XElement Dynamic Property)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

要素について、書式設定されていない XML コンテンツを取得します。  
  
## 構文  
  
```  
elem.Xml  
```  
  
## プロパティ値\/戻り値  
 要素に関する書式設定されていない XML コンテンツを表す <xref:System.String>。  
  
## 解説  
 このプロパティは、`SaveOptions` パラメーターが <xref:System.Xml.Linq.SaveOptions> に設定されている、<xref:System.Xml.Linq.XNode?displayProperty=fullName> クラスの <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29> メソッドに相当します。  
  
## 参照  
 [XElement Class Dynamic Properties](../designers/xelement-class-dynamic-properties.md)   
 [Value](../designers/value-xelement-dynamic-property.md)