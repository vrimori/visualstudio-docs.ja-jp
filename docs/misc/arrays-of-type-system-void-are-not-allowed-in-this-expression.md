---
title: "型 &#39;System.Void&#39; の配列はこの式では使用できません | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31428"
  - "bc31428"
helpviewer_keywords: 
  - "BC31428"
ms.assetid: 21d77b56-585f-4107-b7ec-21933ba58017
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型 &#39;System.Void&#39; の配列はこの式では使用できません
代入ステートメントまたは宣言内の式は、型 <xref:System.Void> の配列を指定します。  
  
 <xref:System.Void> 構造体は、.NET Framework と、特に Visual C\# および Visual C\+\+ によって内部的に使用される特殊な型です。 それは値を返さないメソッドの戻り値の型を指定します。 Visual Basic は、値が返されない場合は `Sub` プロシージャを、値が返される場合は `Function` プロシージャを使用します。  
  
 型 <xref:System.Void> の配列は意味がないため、どのコンテキストでも許可されません。  
  
 **エラー ID:** BC31428  
  
### このエラーを解決するには  
  
1.  配列を指定するかっこを削除します。  
  
2.  実行時の型を <xref:System.Void> と比較する特定の理由がない限り、参照を完全に削除します。  
  
## 参照  
 <xref:System.Void>