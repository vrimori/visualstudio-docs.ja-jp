---
title: "プロパティ アクセサーを &#39;&lt;keyword&gt;&#39; として宣言できません | Microsoft Docs"
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
  - "vbc31099"
  - "bc31099"
helpviewer_keywords: 
  - "BC31099"
ms.assetid: d6f3b989-39b9-4c47-995a-bd83ec03d7b8
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# プロパティ アクセサーを &#39;&lt;keyword&gt;&#39; として宣言できません
`Get` プロシージャまたは `Set` プロシージャの宣言には、プロパティ プロシージャで無効なキーワードが含まれています。  
  
 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement) および [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement) では、アクセス修飾子 \(`Public`、`Protected`、`Friend`、`Protected Friend`、`Private`\) のみが許可されます。  
  
 **エラー ID:** BC31099  
  
### このエラーを解決するには  
  
-   `Get` ステートメントまたは `Set` ステートメントから無効なキーワードを削除します。  
  
## 参照  
 [Property プロシージャ](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)