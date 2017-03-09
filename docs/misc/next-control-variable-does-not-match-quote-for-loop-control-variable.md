---
title: "&#39;Next&#39; コントロール変数が &#39;For&#39; ループ コントロール変数と一致しません | Microsoft Docs"
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
  - "vbc30976"
  - "bc30976"
helpviewer_keywords: 
  - "BC30976"
ms.assetid: 87c2d464-43bf-426f-b78b-7bc07ba171e6
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Next&#39; コントロール変数が &#39;For&#39; ループ コントロール変数と一致しません
`For...Next` ループの `Next` ステートメント内の制御変数は、対応する `For` ステートメント内の変数と一致している必要があります。  
  
 **エラー ID:** BC30976  
  
### このエラーを解決するには  
  
-   `Next` ステートメント内の変数のスペルと、対応する `For` ステートメントの変数のスペルが一致していることを確認します。  
  
-   外側のループの一部を誤って削除していないことを確認します。  
  
-   このループが入れ子になったループ セットの一部になっている場合は、すべてのループが正しく終了していることを確認します。  
  
## 参照  
 [For...Next ステートメント](/dotnet/visual-basic/language-reference/statements/for-next-statement)