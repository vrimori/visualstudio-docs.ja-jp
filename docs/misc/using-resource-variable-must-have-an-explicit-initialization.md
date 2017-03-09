---
title: "&#39;Using&#39; リソース変数には明示的な初期化が必要です | Microsoft Docs"
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
  - "vbc36011"
  - "bc36011"
helpviewer_keywords: 
  - "BC36011"
ms.assetid: 5db996a6-0802-4b67-91f1-4aa9c3dd6b09
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Using&#39; リソース変数には明示的な初期化が必要です
`Using` ステートメントが、`New` 句を使用して初期化していないリソースを少なくとも 1 つ指定しています。  
  
 `Using` ブロックに制御を渡す前にリソースを取得していない場合、`Using` ステートメントはリソースを取得する必要があります。 これには、指定したクラスからオブジェクトを作成する必要があり、`New` 句が必要です。  
  
 **エラー ID:** BC36011  
  
### このエラーを解決するには  
  
-   リソースを既に取得している場合は、取得したリソースと評価される `Using` ステートメントの参照変数か式を使用します。  
  
     `Dim newFont As New System.Drawing.Font`  
  
     `Using newFont`  
  
-   リソースを取得していない場合は、`New` 句を `Using` ステートメントに追加します。  
  
     `Using newFont as`   `New`   `System.Drawing.Font`  
  
## 参照  
 [Using Statement](/dotnet/visual-basic/language-reference/statements/using-statement)   
 [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [How to: Dispose of a System Resource](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)