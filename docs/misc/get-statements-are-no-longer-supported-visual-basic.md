---
title: "&#39;Get&#39; ステートメントは現在サポートされていません (Visual Basic) | Microsoft Docs"
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
  - "vbc30767"
  - "bc30767"
helpviewer_keywords: 
  - "BC30767"
ms.assetid: 6aa62dcc-99aa-4051-a81e-3bbb6a8c355f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Get&#39; ステートメントは現在サポートされていません (Visual Basic)
`Get` ステートメントは現在サポートされていません。 通常、ファイル I\/O 機能は `Microsoft.VisualBasic` 名前空間で使用できますが、.NET Compact Framework のターゲット バージョンではサポートされていません。  
  
 **エラー ID:** BC30767  
  
### このエラーを解決するには  
  
-   <xref:System.IO> 名前空間で定義された関数を使用して、ファイル操作を実行します。  
  
## 参照  
 <xref:System.IO>   
 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [File Access with Visual Basic](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/file-access)