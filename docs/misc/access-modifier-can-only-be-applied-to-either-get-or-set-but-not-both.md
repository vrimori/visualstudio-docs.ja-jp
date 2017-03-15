---
title: "アクセス修飾子は、&#39;Get&#39; または &#39;Set&#39; のいずれか 1 つにのみ適用できますが、両方には適用できません | Microsoft Docs"
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
  - "bc31101"
  - "vbc31101"
helpviewer_keywords: 
  - "BC31101"
ms.assetid: c2a0580c-ff2f-4cc9-9113-6e540f906eec
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# アクセス修飾子は、&#39;Get&#39; または &#39;Set&#39; のいずれか 1 つにのみ適用できますが、両方には適用できません
プロパティ宣言は、[Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)、[Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement)、および [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement) でアクセス レベルを指定します。  
  
 プロパティのアクセス レベルはいつでも指定できます。 さらに、このプロパティのアクセス レベルよりも制限が厳しければ、プロパティ プロシージャ \(`Get` または `Set`\) の 1 つを上限として、異なるアクセス レベルを指定できます。 プロパティ プロシージャの両方にアクセス レベルを指定することはできません。  
  
 **エラー ID:** BC31101  
  
### このエラーを解決するには  
  
-   `Get` ステートメントか `Set` ステートメントからアクセス修飾子を削除します。  
  
## 参照  
 [Property プロシージャ](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)