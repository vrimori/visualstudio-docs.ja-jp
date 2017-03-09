---
title: "&#39;Loop&#39; の前には、対応する &#39;Do&#39; を指定しなければなりません | Microsoft Docs"
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
  - "vbc30091"
  - "bc30091"
helpviewer_keywords: 
  - "BC30091"
ms.assetid: 05f47b2f-4eaa-4911-981e-3fce737d249f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Loop&#39; の前には、対応する &#39;Do&#39; を指定しなければなりません
`Loop` ステートメントが発生していますが、対応する `Do` ステートメントがありません。`Loop` の前に、対応する `Do` ステートメントが必要です。  
  
 **エラー ID:** BC30091  
  
### このエラーを解決するには  
  
1.  この `Do` ループが入れ子になった `Do` ループのセットの一部である場合は、各ループが正しく終了していることを確認します。  
  
2.  `Do` ループ内の他の制御構造が正しく終了していることを確認します。  
  
3.  この `Do` ループが正しく書式設定されていることを確認します。  
  
## 参照  
 [Do...Loop Statement](/dotnet/visual-basic/language-reference/statements/do-loop-statement)