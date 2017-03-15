---
title: "&#39;Sub New&#39; でイベントを処理することはできません | Microsoft Docs"
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
  - "vbc30497"
  - "bc30497"
helpviewer_keywords: 
  - "BC30497"
ms.assetid: b8a546c4-914e-49de-b553-9fc0f41424ed
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Sub New&#39; でイベントを処理することはできません
`Sub New` と `Handles` を結合しようとしていますが、この処理は実行できません。 プロシージャ宣言の最後で `Handles` キーワードを使用すると、`WithEvents` キーワードで宣言されたオブジェクト変数によって発生したイベントが処理されるようになります。  
  
 **エラー ID:** BC30497  
  
### このエラーを解決するには  
  
1.  このコンテキストでは `New` を使用しないでください。  
  
## 参照  
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [WithEvents](/dotnet/visual-basic/language-reference/modifiers/withevents)