---
title: "&#39;End RaiseEvent&#39; は、行の最初のステートメントでなければなりません | Microsoft Docs"
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
  - "vbc31120"
  - "bc31120"
helpviewer_keywords: 
  - "BC31120"
ms.assetid: 51aea522-5c4c-4ec0-8850-03f6ecebd6bc
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End RaiseEvent&#39; は、行の最初のステートメントでなければなりません
`End RaiseEvent` ステートメントの前にコロン \(:\) ステートメント区切り記号があります。`End RaiseEvent` は、そのソース行で唯一のステートメントである必要があります。  
  
 **エラー ID:** BC31120  
  
### このエラーを解決するには  
  
-   複数のステートメントを別々の行に分けます。  
  
## 参照  
 [方法 : コード内でステートメントを分割および連結する](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)   
 [RaiseEvent Statement](/dotnet/visual-basic/language-reference/statements/raiseevent-statement)   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)