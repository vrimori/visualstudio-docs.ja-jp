---
title: "&#39;WriteOnly&#39; として宣言されているプロパティに &#39;Get&#39; を使用することはできません | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30023"
  - "vbc30023"
helpviewer_keywords: 
  - "BC30023"
ms.assetid: ac290f7d-cbc3-4979-a5d9-1ae1bb26e79d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;WriteOnly&#39; として宣言されているプロパティに &#39;Get&#39; を使用することはできません
`Get` プロシージャはプロパティの値を読み取ります。`WriteOnly` プロパティを読み取ることはできません。  
  
 **エラー ID:** BC30023  
  
### このエラーを解決するには  
  
-   `WriteOnly` キーワードを `Property` ステートメントから削除するか、`Get` プロシージャをプロパティ本体から削除します。  
  
## 参照  
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [WriteOnly](/dotnet/visual-basic/language-reference/modifiers/writeonly)