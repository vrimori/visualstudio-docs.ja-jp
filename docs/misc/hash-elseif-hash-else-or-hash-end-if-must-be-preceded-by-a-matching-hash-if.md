---
title: "&#39;#ElseIf&#39;、&#39;#Else&#39;、または &#39;#End If&#39; の前には、対応する &#39;#If&#39; が必要です | Microsoft Docs"
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
  - "vbc30013"
  - "bc30013"
helpviewer_keywords: 
  - "BC30013"
ms.assetid: 8fe2d23c-8b8f-46d8-90f2-7f8857ea43bb
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#ElseIf&#39;、&#39;#Else&#39;、または &#39;#End If&#39; の前には、対応する &#39;#If&#39; が必要です
`#ElseIf`、`#Else`、および `#End If` は条件付きコンパイル ディレクティブです。`#ElseIf`、`#Else`、または `#End If` の前に、対応する `#If` ディレクティブがありません。  
  
 **エラー ID:** BC30013  
  
### このエラーを解決するには  
  
1.  意図した `#If` が、中間の条件付きコンパイル ブロックや、間違って配置された `#End If` によって、問題の句と分離されていないことを確認します。  
  
    > [!NOTE]
    >  各 `#If` ブロックでは `#Else` が 1 つだけ許可されるため、2 つの連続する `#Else` ディレクティブはこのエラーを発生させます。  
  
2.  先頭の `#` が前の `#If` ディレクティブから欠落していないことを確認します。  
  
3.  他のすべての順序が正しい場合、`#If` ディレクティブを条件付きコンパイル ブロックの先頭に追加します。  
  
## 参照  
 [\#If...Then...\#Else Directives](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)