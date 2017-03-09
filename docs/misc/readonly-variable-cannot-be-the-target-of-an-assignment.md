---
title: "&#39;ReadOnly&#39; 変数を代入式のターゲットにすることはできません | Microsoft Docs"
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
  - "vbc30064"
  - "bc30064"
helpviewer_keywords: 
  - "BC30064"
ms.assetid: 17e0751d-4c22-40b2-bb07-cb5c845dbc30
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ReadOnly&#39; 変数を代入式のターゲットにすることはできません
値を代入するコンテキストに `ReadOnly` プロパティがあります。 実行時に値を代入できるのは、書き込み可能な変数、プロパティ、配列要素だけです。  
  
 **エラー ID:** BC30064  
  
### このエラーを解決するには  
  
-   変数を宣言する `Dim` ステートメントから `ReadOnly` キーワードを削除するか、または値を代入するステートメントを削除します。  
  
## 参照  
 [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)   
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)