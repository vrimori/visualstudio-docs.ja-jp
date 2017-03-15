---
title: "&#39;ReadOnly&#39; プロパティには &#39;Get&#39; を指定する必要があります | Microsoft Docs"
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
  - "bc30126"
  - "vbc30126"
helpviewer_keywords: 
  - "BC30126"
ms.assetid: a522c39e-1f11-45c8-a00b-3546c842909a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ReadOnly&#39; プロパティには &#39;Get&#39; を指定する必要があります
プロパティが `ReadOnly` として宣言されている場合は、その値を読み取るためのプロシージャを指定する必要があります。  
  
 **エラー ID:** BC30126  
  
### このエラーを解決するには  
  
1.  `Property` ステートメントと `End Property` ステートメントの間に必ず `Get` プロシージャを含めます。  
  
2.  `Property` 宣言内の他のプロシージャが正しく終了していることを確認します。  
  
## 参照  
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement)