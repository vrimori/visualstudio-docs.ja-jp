---
title: "ステートメントおよびラベルは、&#39;Select Case&#39; と最初の &#39;Case&#39; の間では有効ではありません | Microsoft Docs"
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
  - "bc30058"
  - "vbc30058"
helpviewer_keywords: 
  - "BC30058"
ms.assetid: 399b4659-f7df-4377-80be-43019f1e6206
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ステートメントおよびラベルは、&#39;Select Case&#39; と最初の &#39;Case&#39; の間では有効ではありません
開始の `Select` または `Select Case` ステートメントと最初の `Case` ステートメントの間にコメントではないステートメントがあります。  
  
 **エラー ID:** BC30058  
  
### このエラーを解決するには  
  
-   介在するステートメントがコメントの場合は、先頭にコメント デリミター \(`'` または `REM`\) を指定します。 それ以外の場合は、ステートメントを移動または削除します。  
  
## 参照  
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)