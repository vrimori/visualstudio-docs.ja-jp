---
title: "&#39;&lt;labelname&gt;&#39; は、このステートメントを含まない &#39;Try&#39;、&#39;Catch&#39;、または &#39;Finally&#39; ステートメントの内側にあるため、&#39;GoTo &lt;labelname&gt;&#39; は有効ではありません | Microsoft Docs"
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
  - "bc30754"
  - "vbc30754"
helpviewer_keywords: 
  - "BC30754"
ms.assetid: 2eefc7fb-fdf0-41e9-bf60-c3bc93580e14
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;labelname&gt;&#39; は、このステートメントを含まない &#39;Try&#39;、&#39;Catch&#39;、または &#39;Finally&#39; ステートメントの内側にあるため、&#39;GoTo &lt;labelname&gt;&#39; は有効ではありません
`Try...Catch...Finally` ブロック内に分岐することはできません。  
  
 **エラー ID:** BC30754  
  
### このエラーを解決するには  
  
-   `Try...Catch...Finally` ブロックの前にラベルが配置されるように、コードを再構成します。  
  
## 参照  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)