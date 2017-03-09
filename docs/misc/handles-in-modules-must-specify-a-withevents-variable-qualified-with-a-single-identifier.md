---
title: "モジュールの &#39;Handles&#39; は、単一の識別子で限定された &#39;WithEvents&#39; 変数 を指定しなければなりません | Microsoft Docs"
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
  - "bc31418"
  - "vbc31418"
helpviewer_keywords: 
  - "BC31418"
ms.assetid: 7d866577-1e42-43f1-85d1-5d7eeba881b2
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# モジュールの &#39;Handles&#39; は、単一の識別子で限定された &#39;WithEvents&#39; 変数 を指定しなければなりません
イベント ハンドラーを指定するには、`WithEvents` キーワードで宣言されたオブジェクト変数を `Handles` ステートメントに指定する必要があります。  
  
 **エラー ID:** BC31418  
  
### このエラーを解決するには  
  
-   `WithEvents` 修飾子を使用して、`Handles` ステートメントで使用する変数を宣言します。  
  
## 参照  
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [WithEvents](/dotnet/visual-basic/language-reference/modifiers/withevents)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)