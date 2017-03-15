---
title: "XML コメントに、解決できない &#39;cref&#39; 属性 &#39;&lt;attribute&gt;&#39; が指定されたタグが含まれています | Microsoft Docs"
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
  - "bc42309"
  - "vbc42309"
helpviewer_keywords: 
  - "BC42309"
ms.assetid: c9f3cfa5-565f-48bf-8616-cfb25d24f89e
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML コメントに、解決できない &#39;cref&#39; 属性 &#39;&lt;attribute&gt;&#39; が指定されたタグが含まれています
XML コメントに、解決できない 'cref' 属性 \<attribute\> が指定されたタグが含まれています。 XML コメントは無視されます。  
  
 タグには、識別子の相対名を指定して他の XML 要素へのリンクを指定する `cref` 属性があります。 コンパイル時に、ユーザーが指定した値の修飾 XML 識別子で値が置き換えられます。 コンパイラは、通常の解決規則を使用して、型またはメンバーを検索します。  
  
 **エラー ID:** BC42309  
  
### このエラーを解決するには  
  
-   有効なコード要素を指すように `cref` 属性を検証します。  
  
## 参照  
 [How to: Create XML Documentation](../Topic/How%20to:%20Create%20XML%20Documentation%20in%20Visual%20Basic.md)   
 [XML Comment Tags](/dotnet/visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments)