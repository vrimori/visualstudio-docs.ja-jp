---
title: "&#39;Global&#39; はハンドルで許可されていません。ローカル名を指定してください | Microsoft Docs"
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
  - "bc36002"
  - "vbc36002"
helpviewer_keywords: 
  - "BC36002"
ms.assetid: 7b4602a9-84c9-4068-81bc-e8df03ffc130
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Global&#39; はハンドルで許可されていません。ローカル名を指定してください
`Handles` 句は、ローカル イベントを参照する必要があります。`Global` キーワードにより、グローバルなプログラミング要素にアクセスできるようになります。  
  
 **エラー ID:** BC36002  
  
### このエラーを解決するには  
  
-   グローバル インスタンスではなくイベントのローカル インスタンスを参照するように `Handles` 句を変更します。  
  
## 参照  
 [Global \- delete](http://msdn.microsoft.com/ja-jp/18c8ba14-40f6-4978-8096-6a5852324635)   
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)