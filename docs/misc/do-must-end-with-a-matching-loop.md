---
title: "&#39;Do&#39; の終わりには、対応する &#39;Loop&#39; を指定しなければなりません | Microsoft Docs"
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
  - "vbc30083"
  - "bc30083"
helpviewer_keywords: 
  - "BC30083"
ms.assetid: b157b9e3-57fa-4324-a13d-b37bcf0861e6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Do&#39; の終わりには、対応する &#39;Loop&#39; を指定しなければなりません
`Do` ステートメントが発生していますが、対応する `Loop` ステートメントがありません。`Loop` ステートメントを使用して、`Do` ループを終了する必要があります。  
  
 **エラー ID:** BC30083  
  
### このエラーを解決するには  
  
-   この `Do` ループが入れ子になったループのセットの一部である場合は、各ループが正しく終了していることを確認します。  
  
-   `Loop` ステートメントを `Do` ループの最後に追加します。  
  
## 参照  
 [Do...Loop Statement](/dotnet/visual-basic/language-reference/statements/do-loop-statement)