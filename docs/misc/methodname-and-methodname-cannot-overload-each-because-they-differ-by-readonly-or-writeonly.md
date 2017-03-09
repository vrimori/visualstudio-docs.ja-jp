---
title: "&lt;methodname&gt;&#39; と &#39;&lt;methodname&gt;&#39; では、&#39;ReadOnly&#39; であるか、または &#39;WriteOnly&#39; であるかのみが異なるため、お互いをオーバーロードすることはできません | Microsoft Docs"
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
  - "vbc30366"
  - "BC30366"
helpviewer_keywords: 
  - "BC30366"
ms.assetid: 2440fd29-e205-4004-b2ee-9d954d17b8d3
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;methodname&gt;&#39; と &#39;&lt;methodname&gt;&#39; では、&#39;ReadOnly&#39; であるか、または &#39;WriteOnly&#39; であるかのみが異なるため、お互いをオーバーロードすることはできません
`ReadOnly` および `WriteOnly` 宣言のみが異なる 2 つのメソッドをオーバーロードしようとしました。 引数リスト以外のものを使用して、バージョンを区別することはできません。  
  
 **エラー ID:** BC30366  
  
### このエラーを解決するには  
  
-   メソッドが `ReadOnly` および `WriteOnly` 以外のもので区別されていることを確認します。  
  
## 参照  
 [Considerations in Overloading Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)