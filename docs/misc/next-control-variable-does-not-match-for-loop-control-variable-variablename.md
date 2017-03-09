---
title: "Next コントロール変数が For ループ コントロール変数 &#39;&lt;variablename&gt;&#39; と一致しません | Microsoft Docs"
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
  - "vbc30070"
  - "bc30070"
helpviewer_keywords: 
  - "BC30070"
ms.assetid: e9e96008-b053-4fa0-8966-decaad99fecd
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Next コントロール変数が For ループ コントロール変数 &#39;&lt;variablename&gt;&#39; と一致しません
`For...Next` ループの `Next` ステートメント内のコントロール変数は、対応する `For` ステートメント内の変数と一致している必要があります。  
  
 **エラー ID:** BC30070  
  
### このエラーを解決するには  
  
1.  `Next` ステートメント内の変数のスペルと、対応する `For` ステートメントの変数のスペルが一致していることを確認します。  
  
2.  外側のループの一部を誤って削除していないことを確認します。  
  
3.  このループが、入れ子になったループ セットの一部である場合は、すべてのループが正しく終了しているかどうかを確認します。  
  
## 参照  
 [For...Next ステートメント](/dotnet/visual-basic/language-reference/statements/for-next-statement)