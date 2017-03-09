---
title: "&#39;&lt;property1&gt;&#39; と &#39;&lt;property2&gt;&#39; では、一方のみが &#39;Default&#39; に宣言されているため、お互いをオーバーロードすることはできません。 | Microsoft Docs"
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
  - "bc30361"
  - "vbc30361"
helpviewer_keywords: 
  - "BC30361"
ms.assetid: bac85b32-1a1f-4c43-817c-76e209cfeb8c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;property1&gt;&#39; と &#39;&lt;property2&gt;&#39; では、一方のみが &#39;Default&#39; に宣言されているため、お互いをオーバーロードすることはできません。
プロパティで `Default` が指定されている場合、その名前でオーバーロードされたすべてのプロパティでも `Default` を指定する必要があります。  
  
 **エラー ID:** BC30361  
  
### このエラーを解決するには  
  
-   オーバーロードされたプロパティがすべて `Default` として宣言されていることを確認します。  
  
## 参照  
 [Considerations in Overloading Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)   
 [Default](/dotnet/visual-basic/language-reference/modifiers/default)