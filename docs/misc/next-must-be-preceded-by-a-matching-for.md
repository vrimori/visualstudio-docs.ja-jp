---
title: "&#39;Next&#39; の前には、対応する &#39;For&#39; を指定しなければなりません | Microsoft Docs"
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
  - "vbc30092"
  - "bc30092"
helpviewer_keywords: 
  - "BC30092"
ms.assetid: 4bf49bb2-c69b-443d-aa58-cb40fcfb1370
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Next&#39; の前には、対応する &#39;For&#39; を指定しなければなりません
`Next` ステートメントが発生していますが、対応する `For` または `For Each` ステートメントがありません。`Next` の前に、対応する `For` または `For Each` ステートメントを指定してください。  
  
 **エラー ID:** BC30092  
  
### このエラーを解決するには  
  
1.  この `For` ループが入れ子になった `For` ループのセットの一部である場合は、各ループが正しく終了していることを確認します。  
  
2.  `For` ループ内の他の制御構造が正しく終了していることを確認します。  
  
3.  この `For` ループが正しく書式設定されていることを確認します。  
  
## 参照  
 [For...Next ステートメント](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [For Each...Next ステートメント](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)