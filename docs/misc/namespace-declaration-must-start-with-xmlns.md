---
title: "名前空間宣言は &#39;xmlns&#39; で始まらなければなりません。 | Microsoft Docs"
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
  - "bc31187"
  - "vbc31187"
helpviewer_keywords: 
  - "BC31187"
ms.assetid: 64c6a033-7cdc-48a0-bff0-bdd045cb13ad
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 名前空間宣言は &#39;xmlns&#39; で始まらなければなりません。
XML 名前空間が、必要な `xmlns` 識別子を使用せずに指定されています。`xmlns` 識別子には、小文字のみを含める必要があります。  
  
 **エラー ID:** BC31187  
  
### このエラーを解決するには  
  
-   XML 名前空間を宣言する場合は、`xmlns` 識別子を使用します。 例を次に示します。  
  
    ```vb#  
    Imports <xmlns:ns="http://SampleNamespace">  
    ```  
  
## 参照  
 [Imports Statement \(XML Namespace\)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)   
 [XML Literals](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)