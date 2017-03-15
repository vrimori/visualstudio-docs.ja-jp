---
title: "&#39;Finally&#39; からの分岐は有効ではありません | Microsoft Docs"
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
  - "bc30101"
  - "vbc30101"
helpviewer_keywords: 
  - "BC30101"
ms.assetid: 16a0dc29-3657-4373-b77f-38f3cb80e6c9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Finally&#39; からの分岐は有効ではありません
`Finally` ブロック内の `GoTo` ステートメントが、ブロック外に分岐しています。`Catch` ブロックまたは `Finally` ブロックの中へ、またはそれらのブロックから外へ分岐するのは正しくありません。  
  
 **エラー ID:** BC30101  
  
### このエラーを解決するには  
  
-   `GoTo` ステートメントを削除し、条件判断構造またはループ制御構造を使用するプログラム ロジックの実装をご検討ください。  
  
## 参照  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [GoTo Statement](/dotnet/visual-basic/language-reference/statements/goto-statement)   
 [Control Flow](/dotnet/visual-basic/programming-guide/language-features/control-flow/index)