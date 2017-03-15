---
title: "&#39;#Else&#39; の前には、対応する &#39;#If&#39; または &#39;#ElseIf&#39; を指定しなければなりません | Microsoft Docs"
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
  - "vbc30028"
  - "bc30028"
helpviewer_keywords: 
  - "BC30028"
ms.assetid: c6ed34de-d6ed-4227-9880-538055aff20a
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#Else&#39; の前には、対応する &#39;#If&#39; または &#39;#ElseIf&#39; を指定しなければなりません
`#Else` は条件付きコンパイル ディレクティブです。`#Else` ディレクティブの前に、対応する `#If` または `#ElseIf` がありません。  
  
 **エラー ID:** BC30028  
  
### このエラーを解決するには  
  
1.  先行する `#If` または `#ElseIf` が、中間の条件付きコンパイル ブロックまたは正しくない位置にある `#End If` によって、この `#Else` と分離されないことを確認します。  
  
2.  `#Else` の前に別の `#Else` ディレクティブが指定されていることを確認します。 指定されている場合は、`#Else` を削除するか、`#ElseIf` に変更します。  
  
3.  他のすべての順序が正しい場合、`#If` ディレクティブを条件付きコンパイル ブロックの先頭に追加します。  
  
## 参照  
 [\#If...Then...\#Else Directives](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)