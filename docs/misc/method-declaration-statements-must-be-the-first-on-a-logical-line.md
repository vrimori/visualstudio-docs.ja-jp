---
title: "メソッド宣言ステートメントは論理行の最初のステートメントでなければなりません | Microsoft Docs"
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
  - "bc32009"
  - "vbc32009"
helpviewer_keywords: 
  - "BC32009"
ms.assetid: 77275387-5584-4419-aee3-a1b600f0412d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# メソッド宣言ステートメントは論理行の最初のステートメントでなければなりません
`Function` または `Sub` ステートメントがコロン \(:\) ステートメント区切り文字の後に続いています。`Function` または `Sub` は、そのソース行でただ 1 つのステートメントである必要があります。  
  
 **エラー ID:** BC32009  
  
### このエラーを解決するには  
  
-   複数のステートメントを別々の行に分けます。  
  
## 参照  
 [方法 : コード内でステートメントを分割および連結する](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)   
 [Sub Statement](/dotnet/visual-basic/language-reference/statements/sub-statement)   
 [Function Statement](/dotnet/visual-basic/language-reference/statements/function-statement)