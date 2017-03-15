---
title: "&#39;prefix&#39; は XML プレフィックスであり、式として使用することはできません | Microsoft Docs"
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
  - "bc30114"
  - "vbc30114"
helpviewer_keywords: 
  - "BC30114"
ms.assetid: 5cb7c89e-c61b-483a-9369-5285b7cbcf45
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;prefix&#39; は XML プレフィックスであり、式として使用することはできません
'prefix' は XML プレフィックスであり、式として使用することはできません。 GetXmlNamespace 演算子を使用して、名前空間オブジェクトを作成します。  
  
 `Imports` ステートメントを使用してインポートされる XML 名前空間のプレフィックスは、XML リテラルの外側では使用できません。  
  
 **エラー ID:** BC30114  
  
### このエラーを解決するには  
  
-   インポートされた XML 名前空間の部分を参照する必要がある場合は、`GetXmlNamespace` 演算子を使用して <xref:System.Xml.Linq.XNamespace> オブジェクトを取得します。 このオブジェクトを、XML 名前空間プレフィックスの代わりに使用します。  
  
-   XML リテラルを修飾するために XML 名前空間プレフィックスを使用している場合は、XML リテラルの適切な構文を使用していることを確認します。  
  
## 参照  
 [XML Literals](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [Imports Statement \(XML Namespace\)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)   
 [GetXmlNamespace Operator](/dotnet/visual-basic/language-reference/operators/getxmlnamespace-operator)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)