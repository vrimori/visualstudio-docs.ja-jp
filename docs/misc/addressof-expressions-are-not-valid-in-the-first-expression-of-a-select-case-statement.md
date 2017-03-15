---
title: "&#39;AddressOf&#39; 式は、&#39;Select Case&#39; ステートメントの最初の式では有効ではありません | Microsoft Docs"
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
  - "bc36636"
  - "vbc36636"
helpviewer_keywords: 
  - "BC36636"
ms.assetid: 2ccc0ccc-d4d0-4910-8859-dedfa57c8126
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;AddressOf&#39; 式は、&#39;Select Case&#39; ステートメントの最初の式では有効ではありません
`AddressOf` 式は、`Select Case` ステートメントのテスト式に使用できません。`AddressOf` 式は関数デリゲートを返しますが、`Select Case` ステートメントのテスト式は基本データ型である必要があります。  
  
 **エラー ID:** BC36636  
  
### このエラーを解決するには  
  
-   コードを調べて、`If...Then...Else` ステートメントなどの別の条件構造を使用できないかをご確認ください。  
  
## 参照  
 [AddressOf Operator](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [If...Then...Else Statement](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)   
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)