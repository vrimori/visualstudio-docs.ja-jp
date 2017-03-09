---
title: "&#39;Next&#39; が必要です | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30003"
  - "bc30003"
helpviewer_keywords: 
  - "BC30003"
ms.assetid: 75a68984-decd-43e2-808a-f14b36dd2c60
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Next&#39; が必要です
終端の `Next` がない状態で `On Error Resume` コンストラクトが指定されています。  
  
 **エラー ID:** BC30003  
  
### このエラーを解決するには  
  
-   `On Error` ステートメントの末尾に `Next` キーワードを追加します。  
  
## 参照  
 [On Error Statement](/dotnet/visual-basic/language-reference/statements/on-error-statement)   
 [Error Statement](/dotnet/visual-basic/language-reference/statements/error-statement)   
 [Resume Statement](/dotnet/visual-basic/language-reference/statements/resume-statement)   
 [非構造化例外処理の概要 \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/d2d84b66-ff3a-4878-a578-484c0c6d5c3d)