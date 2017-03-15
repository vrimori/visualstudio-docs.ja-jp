---
title: "イベント &#39;&lt;eventname&gt;&#39; に対して、&#39;AddHandler&#39; 定義がありません。 | Microsoft Docs"
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
  - "bc31130"
  - "vbc31130"
helpviewer_keywords: 
  - "BC31130"
ms.assetid: cf6c7fd6-ce2e-4916-b427-2a4a63e7279d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# イベント &#39;&lt;eventname&gt;&#39; に対して、&#39;AddHandler&#39; 定義がありません。
イベントが `Custom` として宣言されている場合、イベント ハンドラーを追加するためのプロシージャを指定する必要があります。  
  
 **エラー ID:** BC31130  
  
### このエラーを解決するには  
  
1.  `Custom Event` ステートメントと `End Event` ステートメントの間に `AddHandler` 宣言を含めます。  
  
2.  イベント宣言内の他のプロシージャが適切に終了したことを確認します。  
  
## 参照  
 [AddHandler Statement](/dotnet/visual-basic/language-reference/statements/addhandler-statement)   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)