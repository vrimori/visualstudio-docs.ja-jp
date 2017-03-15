---
title: "イベント &#39;&lt;eventname&gt;&#39; に対して &#39;RaiseEvent&#39; 定義が指定されていません | Microsoft Docs"
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
  - "vbc31132"
  - "bc31132"
helpviewer_keywords: 
  - "BC31132"
ms.assetid: 8f3442fd-2ed1-4dbc-83a8-f0860ec022ac
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# イベント &#39;&lt;eventname&gt;&#39; に対して &#39;RaiseEvent&#39; 定義が指定されていません
イベントが `Custom` として宣言されている場合、イベントを発生させるためのプロシージャを指定する必要があります。  
  
 **エラー ID:** BC31132  
  
### このエラーを解決するには  
  
1.  `Custom Event` ステートメントと `End Event` ステートメントの間に `RaiseEvent` 宣言を含めます。  
  
2.  イベント宣言内の他のプロシージャが適切に終了することを確認します。  
  
## 参照  
 [RaiseEvent Statement](/dotnet/visual-basic/language-reference/statements/raiseevent-statement)   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)