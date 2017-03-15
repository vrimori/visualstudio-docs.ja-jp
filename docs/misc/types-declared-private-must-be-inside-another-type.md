---
title: "&#39;Private&#39; と宣言された型は、別の型の内部になければなりません | Microsoft Docs"
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
  - "vbc31089"
  - "bc31089"
helpviewer_keywords: 
  - "BC31089"
ms.assetid: 44ea5fe4-4af6-4cea-a4a5-2cf966df2937
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Private&#39; と宣言された型は、別の型の内部になければなりません
`Private` 修飾子が別の型の内部にない型で使用されました。  
  
 **エラー ID:** BC31089  
  
### このエラーを解決するには  
  
1.  `Friend` などの制限の緩いアクセス修飾子を使用します。  
  
2.  別の型の内部で型を宣言します。  
  
## 参照  
 [Private](/dotnet/visual-basic/language-reference/modifiers/private)