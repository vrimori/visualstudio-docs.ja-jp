---
title: "&#39;Exit&#39; の後には、&#39;Sub&#39;、&#39;Function&#39;、&#39;Property&#39;、&#39;Do&#39;、&#39;For&#39;、&#39;While&#39;、&#39;Select&#39;、または &#39;Try&#39; を指定しなければなりません | Microsoft Docs"
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
  - "bc30240"
  - "vbc30240"
helpviewer_keywords: 
  - "BC30240"
ms.assetid: 91078689-f4bf-4331-a475-10bc9fe7cd0c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit&#39; の後には、&#39;Sub&#39;、&#39;Function&#39;、&#39;Property&#39;、&#39;Do&#39;、&#39;For&#39;、&#39;While&#39;、&#39;Select&#39;、または &#39;Try&#39; を指定しなければなりません
`Exit` ステートメントに無効なキーワードが含まれています。`Exit` は、ブロックに続くステートメントに制御が転送されるブロックを指定する必要があります。たとえば、`End While` です。  
  
 **エラー ID:** BC30240  
  
### このエラーを解決するには  
  
-   `Exit` に続く有効なキーワードを追加するか、または `Exit` ステートメントを削除します。  
  
## 参照  
 [Exit Statement](/dotnet/visual-basic/language-reference/statements/exit-statement)