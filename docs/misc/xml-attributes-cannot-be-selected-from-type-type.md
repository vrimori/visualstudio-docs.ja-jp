---
title: "XML 属性を型 &#39;type&#39; から選択することはできません | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36808"
  - "vbc36808"
helpviewer_keywords: 
  - "BC36808"
ms.assetid: 76b2605c-3d9b-4e56-ba3f-99c60c668290
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML 属性を型 &#39;type&#39; から選択することはできません
型が <xref:System.Xml.Linq.XElement> または `IEnumerable(Of XElement)` ではないオブジェクトについては、XML 属性が参照されています。 詳細については、「[XML Attribute Axis Property](/dotnet/visual-basic/language-reference/xml-axis/xml-attribute-axis-property)」を参照してください。  
  
```vb#  
' Generates an error. Dim var = "sample text".@attr  
```  
  
 **エラー ID:** BC36808  
  
### このエラーを解決するには  
  
-   属性を参照しているオブジェクトが、<xref:System.Xml.Linq.XElement> または `IEnumerable(Of XElement)` として厳密に型指定されていることを確認してください。 例を次に示します。  
  
    ```vb#  
    Dim elem As XElement = <root attr="value"/> Dim var = elem.@attr  
    ```  
  
## 参照  
 [XML Attribute Axis Property](/dotnet/visual-basic/language-reference/xml-axis/xml-attribute-axis-property)   
 [XML Axis Properties](/dotnet/visual-basic/language-reference/xml-axis/xml-axis-properties)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)