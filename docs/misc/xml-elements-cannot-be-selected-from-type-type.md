---
title: "XML 要素を型 &#39;type&#39; から選択することはできません。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36807"
  - "bc36807"
helpviewer_keywords: 
  - "BC36807"
ms.assetid: 01c19899-2b44-41e9-a99c-35edfa0deaf1
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML 要素を型 &#39;type&#39; から選択することはできません。
型が <xref:System.Xml.Linq.XElement>、<xref:System.Xml.Linq.XDocument>、または `IEnumerable(Of XElement)` ではないオブジェクトについては、XML 子要素が参照されています。 詳細については、「[XML Child Axis Property](/dotnet/visual-basic/language-reference/xml-axis/xml-child-axis-property)」を参照してください。  
  
```vb#  
' Generates an error. Dim var = "sample text".<child>  
```  
  
 **エラー ID:** BC36807  
  
### このエラーを解決するには  
  
-   参照している属性を含むオブジェクトが、<xref:System.Xml.Linq.XElement>、<xref:System.Xml.Linq.XDocument>、または `IEnumerable(Of XElement)` として厳密に型指定されていることを確認してください。 例を次に示します。  
  
    ```vb#  
    Dim elem As XElement = <root> <child /> </root> Dim var = elem.<child>  
    ```  
  
## 参照  
 [XML Child Axis Property](/dotnet/visual-basic/language-reference/xml-axis/xml-child-axis-property)   
 [XML Axis Properties](/dotnet/visual-basic/language-reference/xml-axis/xml-axis-properties)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)