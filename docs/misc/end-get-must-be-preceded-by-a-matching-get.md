---
title: "&#39;End Get&#39; の前には、対応する &#39;Get&#39; を指定しなければなりません | Microsoft Docs"
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
  - "bc30630"
  - "vbc30630"
helpviewer_keywords: 
  - "BC30630"
ms.assetid: d858076a-9088-4ad0-9766-95029476bf9b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Get&#39; の前には、対応する &#39;Get&#39; を指定しなければなりません
`Get` プロパティ プロシージャを終了するには、`End Get` を使用します。`Get` プロパティ プロシージャの外側に `End Get` コンストラクトが見つかりました。  
  
 **エラー ID:** BC30630  
  
### このエラーを解決するには  
  
1.  `Get` プロパティ プロシージャが `Property` キーワードの後かつ `End Property` コンストラクトの前に宣言されていることを確認します。  
  
2.  `Get` プロパティ プロシージャが `Get` キーワードで始まり、`End Get` コンストラクトで終わっていることを確認します。  
  
## 参照  
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Property Changes in Visual Basic](http://msdn.microsoft.com/ja-jp/1c138efa-9bc2-44d7-80a0-f3a7c2510264)