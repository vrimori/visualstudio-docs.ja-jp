---
title: "&#39;End RemoveHandler&#39; は、行の最初のステートメントでなければなりません | Microsoft Docs"
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
  - "bc31119"
  - "vbc31119"
helpviewer_keywords: 
  - "BC31119"
ms.assetid: 4a7e2a71-02d1-41fe-a126-3674288e6efc
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End RemoveHandler&#39; は、行の最初のステートメントでなければなりません
`End RemoveHandler` ステートメントがコロン \(:\) ステートメント区切り文字の後に続いています。`End RemoveHandler` はそのソース行でただ 1 つのステートメントである必要があります。  
  
 **エラー ID:** BC31119  
  
### このエラーを解決するには  
  
-   複数のステートメントを別々の行に分けます。  
  
## 参照  
 [方法 : コード内でステートメントを分割および連結する](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)   
 [RemoveHandler Statement](/dotnet/visual-basic/language-reference/statements/removehandler-statement)   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)