---
title: "XML コメント タグ &#39;returns&#39; は、&#39;declare sub&#39; 言語要素では許可されていません | Microsoft Docs"
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
  - "bc42315"
  - "vbc42315"
helpviewer_keywords: 
  - "BC42315"
ms.assetid: 55ba3e8a-ba7f-42e3-a4a7-b22844e72564
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML コメント タグ &#39;returns&#39; は、&#39;declare sub&#39; 言語要素では許可されていません
XML コメント タグ 'returns' は、'declare sub' 言語要素では許可されていません。 XML コメントは無視されます。  
  
 `Declare Sub` 宣言に対する XML コメントに、`<`returns`>` タグを含めることはできません。  
  
 **エラー ID:** BC42315  
  
### このエラーを解決するには  
  
-   サポートされていない `<`returns`>` タグを削除します。  
  
## 参照  
 [\<returns\>](../Topic/%3Creturns%3E%20\(Visual%20Basic\).md)   
 [XML Comment Tags](/dotnet/visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments)   
 [Documenting Your Code with XML](/dotnet/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml)   
 [Declare Statement](/dotnet/visual-basic/language-reference/statements/declare-statement)