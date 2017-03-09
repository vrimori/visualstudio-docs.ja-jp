---
title: "Function、Get または Operator の &#39;Return&#39; ステートメントは、値を返さなければなりません | Microsoft Docs"
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
  - "bc30654"
  - "vbc30654"
helpviewer_keywords: 
  - "BC30654"
ms.assetid: af0fb1fc-1b2e-4cae-9768-10965cda5506
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Function、Get または Operator の &#39;Return&#39; ステートメントは、値を返さなければなりません
`Return` ステートメントは、呼び出し元のプロシージャに値を返すときに使用しなければなりません。 プログラム フローを制御するために単独で `Return` ステートメントを使うことはできません。  
  
 **エラー ID:** BC30654  
  
### このエラーを解決するには  
  
1.  関数またはプロシージャが返すことができる値を指定します。  
  
2.  プログラムで現在のプロシージャを終了するには、`End` ステートメントを使います。  
  
## 参照  
 [Return Statement](/dotnet/visual-basic/language-reference/statements/return-statement)   
 [End \<keyword\> Statement](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)