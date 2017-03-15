---
title: "&#39;#If&#39; ブロックの一部として &#39;#ElseIf&#39; を &#39;#Else&#39; の後に使用することはできません | Microsoft Docs"
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
  - "bc32030"
  - "vbc32030"
helpviewer_keywords: 
  - "BC32030"
ms.assetid: 248d6464-3019-4753-8a33-7070bbe5d2a6
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#If&#39; ブロックの一部として &#39;#ElseIf&#39; を &#39;#Else&#39; の後に使用することはできません
`#ElseIf` 条件付きコンパイル ディレクティブが `#Else` ディレクティブの後に続いています。`#Else` は、`#End If` ディレクティブの前で、条件付きブロックの最後のディレクティブである必要があります。  
  
 **エラー ID:** BC32030  
  
### このエラーを解決するには  
  
1.  先行する `#Else` が `#ElseIf` である必要があるかどうかを確認します。  
  
2.  先行する `#If` ブロックが正しく終了し、新しい `#If` ブロックを開始することを確認します。  
  
3.  他のすべてが正しい場合は、この `#ElseIf` ディレクティブと対応するステートメントをブロックを移動して、`#Else` ブロックの前に配置します。  
  
## 参照  
 [\#If...Then...\#Else Directives](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)