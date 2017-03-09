---
title: "&#39;Next&#39; ステートメントは、対応する &#39;For&#39; ステートメントよりも多い変数を指定しています | Microsoft Docs"
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
  - "bc32037"
  - "vbc32037"
helpviewer_keywords: 
  - "BC32037"
ms.assetid: 7c97d835-1043-40ec-a645-63a053f5f916
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Next&#39; ステートメントは、対応する &#39;For&#39; ステートメントよりも多い変数を指定しています
入れ子になったループが単一の `Next` ステートメントで終了していますが、このステートメントでは、次の例のように、入れ子内にあるループよりも多くのループ変数を指定しています。  
  
```  
For I = 1 To 10 For J = 1 To 5 ' ... Next J, I, K   ' Next J, I is valid, but there is no loop on K.  
```  
  
 **エラー ID:** BC32037  
  
### このエラーを解決するには  
  
1.  `Next` ステートメントでは、入れ子になったすべてのループ変数をループ開始の逆順で指定していることを確認します。  
  
2.  `Next` ステートメントから余分な変数を削除します。  
  
## 参照  
 [For...Next ステートメント](/dotnet/visual-basic/language-reference/statements/for-next-statement)