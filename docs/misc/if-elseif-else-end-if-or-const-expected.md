---
title: "&#39;If&#39;、&#39;ElseIf&#39;、&#39;Else&#39;、&#39;End If&#39;、または &#39;Const&#39; が必要です | Microsoft Docs"
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
  - "vbc30248"
  - "bc30248"
helpviewer_keywords: 
  - "BC30248"
ms.assetid: fa3bf591-8036-459c-8c29-ed7784e444f6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;If&#39;、&#39;ElseIf&#39;、&#39;Else&#39;、&#39;End If&#39;、または &#39;Const&#39; が必要です
ソース行は `#` 文字で始まりますが、有効な条件付きコンパイル ディレクティブが `#` のすぐ後に続きません。 有効なディレクティブには、`#Const`、`#ExternalSource`、`#If`、`#Else`、`#ElseIf`、`#End If`、および `#Region` があります。  
  
 **エラー ID:** BC30248  
  
### このエラーを解決するには  
  
1.  条件付きコンパイル ディレクティブのスペルが正しいことを確認します。  
  
2.  `#` 文字とディレクティブの間に空白がないことを確認します。  
  
3.  `#` 文字を削除するか、またはすぐ後ろに有効なディレクティブを追加します。  
  
## 参照  
 [Directives](/dotnet/visual-basic/language-reference/directives/directives)