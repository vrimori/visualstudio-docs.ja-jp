---
title: "プロパティ アクセサーを &#39;Default&#39; プロパティ内で &#39;&lt;accessmodifier&gt;&#39; として宣言できません | Microsoft Docs"
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
  - "bc31107"
  - "vbc31107"
helpviewer_keywords: 
  - "BC31107"
ms.assetid: 25657b33-df85-4535-8043-69795c987175
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# プロパティ アクセサーを &#39;Default&#39; プロパティ内で &#39;&lt;accessmodifier&gt;&#39; として宣言できません
既定のプロパティの [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement) または [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement) に、`Private` キーワードが含まれています。  
  
 既定のプロパティを `Private` にすることはできません、また、個々の property プロシージャ \(`Get` または `Set`\) にすることもできません。  
  
 **エラー ID:** BC31107  
  
### このエラーを解決するには  
  
-   `Private` キーワードを `Get` ステートメントまたは `Set` ステートメントから削除するか、`Default` を [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement) から削除します。  
  
## 参照  
 [Property プロシージャ](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)   
 [How to: Declare and Call a Default Property in Visual Basic](../Topic/How%20to:%20Declare%20and%20Call%20a%20Default%20Property%20in%20Visual%20Basic.md)