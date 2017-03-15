---
title: "アクセス修飾子 &#39;&lt;accessmodifier&gt;&#39; は無効です | Microsoft Docs"
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
  - "bc31100"
  - "vbc31100"
helpviewer_keywords: 
  - "BC31100"
ms.assetid: 1cd71acc-0b54-4f64-8d61-75b272d293cb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# アクセス修飾子 &#39;&lt;accessmodifier&gt;&#39; は無効です
[Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement) または [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement) は、包含するプロパティに指定されているより制限の緩いアクセス レベルを指定します。  
  
 プロパティのアクセス レベルはいつでも指定できます。 さらに、このプロパティのアクセス レベルよりも制限が厳しければ、プロパティ プロシージャ \(`Get` または `Set`\) の 1 つを上限として、異なるアクセス レベルを指定できます。 たとえば、プロパティが `Friend` の場合、プロパティ プロシージャに対して `Public` ではなく、`Private` を指定できます。 プロパティ プロシージャの両方にアクセス レベルを指定することはできません。  
  
 **エラー ID:** BC31100  
  
### このエラーを解決するには  
  
-   プロパティ プロシージャのアクセス レベルをプロパティよりも厳しくするか、またはアクセス修飾子を完全に削除します。  
  
-   [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement) で制限の緩いアクセス レベルを宣言し、プロパティ プロシージャのいずれかに、より制限の厳しいアクセス レベルを宣言します。  
  
## 参照  
 [Property プロシージャ](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)