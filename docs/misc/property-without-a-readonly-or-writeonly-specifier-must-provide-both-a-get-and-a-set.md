---
title: "&#39;ReadOnly&#39; または &#39;WriteOnly&#39; 指定子を持たないプロパティには、&#39;Get&#39; と &#39;Set&#39; の両方を指定する必要があります | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30124"
  - "vbc30124"
helpviewer_keywords: 
  - "BC30124"
ms.assetid: b24fc997-9a6b-44d1-b712-dab498a6fc72
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ReadOnly&#39; または &#39;WriteOnly&#39; 指定子を持たないプロパティには、&#39;Get&#39; と &#39;Set&#39; の両方を指定する必要があります
プロパティが `ReadOnly` または `WriteOnly` で宣言されていない場合、値の読み取りと書き込みのためにプロシージャを指定する必要があります。  
  
 **エラー ID:** BC30124  
  
### このエラーを解決するには  
  
1.  `Property` ステートメントと `End Property` ステートメントの間に `Get` プロシージャと `Set` プロシージャの両方を必ず含めます。  
  
2.  `Property` 宣言内の他のプロシージャが適切に終了することを確認します。  
  
## 参照  
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement)